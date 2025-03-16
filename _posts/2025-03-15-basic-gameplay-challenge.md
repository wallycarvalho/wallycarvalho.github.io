---
layout: post
title: Implementing Basic Gameplay mission from Unity3D
date: 2025-03-15 08:00:00
description: Devlog on completing the basic gameplay mission on Unity
tags: career gamedev unity3d ui-slider healthbar
categories: journal
thumbnail: assets/img/animal-feeder.png
---


For the first time in a long while, I felt that drive—the kind that, as a programmer, _**keeps you glued to your seat**_ until you solve an issue. The drive that stays with you, swirling in your mind day and night. Even though I ended up missing dinner on Friday night, I’ve never felt so happy to experience it. It’s been so long since I’ve felt so immersed and consumed by solving programming puzzles and creating exciting things.


## The game

The purpose of this game was to leverage the provided environment and assets to programmatically create logic for detecting collisions, handling interactions between elements (such as projectiles hitting animals), implementing shooting mechanisms, managing UI, and providing player feedback. The video below shows the final project recording. The left portion of the layout is split between the scene view and game view at the bottom. The console, shown in the bottom right corner, displays game information including the player's lives, detected collisions, and life bonuses earned when successfully feeding animals.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/animal-feeder.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
<div class="caption">
    A demonstration of the full Animal Feeder game with animal health bars (UI Sliders) attached to each animal prefab.
</div>


## Player Controller

The player controller grew exponentially since the last exercise. Since then, I had to:
- Introduce a new standalone C# object to manage the player's lives
- Introduce vertical and horizontal movements so the player can freely move their character and avoid collisions
- Avoid moving outside boundaries
- Address boundary bugs (both player, animals, and projectiles)
- Introduce public methods to allow other classes to find the player controller game object so they can call and handle collision events (player lives events)

Here's the full implementation
{% highlight c# linenos %}
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    private float horizontalInput;
    private float verticalInput;
    private float speed = 10.0f;
    private float xRange = 19.0f;
    private float zRange = 13.0f;
    public GameObject projectilePrefab;
    private float fireRate = 0.25f;
    private float nextFire = 0.0f;
    private bool hasNotifiedPlayer = false;

    private PlayerLives playerLives;
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        playerLives = new PlayerLives();
    }

    // Update is called once per frame
    void Update()
    {
        horizontalInput = Input.GetAxis("Horizontal");
        verticalInput = Input.GetAxis("Vertical");
        transform.Translate(Vector3.right * horizontalInput * Time.deltaTime * speed);
        transform.Translate(Vector3.forward * verticalInput * Time.deltaTime * speed);

        // if value on X axis is beyond the minimum or maximum
        // we clamp to set a stopper value that makes sure the
        // player does not go beyond the set value
        if (transform.position.x < -xRange || transform.position.x > xRange)
        {
            float clampedX = Mathf.Clamp(transform.position.x, -xRange, xRange);
            transform.position = new Vector3(clampedX, transform.position.y, transform.position.z);
        }


        // set the a Z stopper value so the player does not go beyond the set value
        if (transform.position.z < -zRange)
        {
            transform.position = new Vector3(transform.position.x, transform.position.y, -zRange);
        }

        // if the player presses space, we instantiate a new projectile
        // at the player's position and rotation so it moves forward
        if (Input.GetKey(KeyCode.Space) && Time.time > nextFire)
        {
            Instantiate(projectilePrefab, transform.position, projectilePrefab.transform.rotation);
            nextFire = Time.time + fireRate;
        }
    }

    // LoseLife achieves two main goals:
    // first it checks if the player has no more lives
    // if the player has no more lives, we destroy the player object
    // and notify the player that they have no more lives but only once
    public void LoseLife()
    {
        if (playerLives.Lives <= 0 && hasNotifiedPlayer == false)
        {
            hasNotifiedPlayer = true;
            Debug.Log("Game Over! Player has no more lives.");
        }
        else if (playerLives.Lives > 0)
        {
            playerLives.LoseLife();
            Debug.Log("Player lost a life. Remaining lives: " + playerLives.Lives);
        }
    }

    // GetLives returns the number of lives the player has
    public int GetLives()
    {
        return playerLives.Lives;
    }

    // GainLife adds a life to the player and logs the result so the player can see in Unity's console
    public void GainLife()
    {
        playerLives.GainLife();
        Debug.Log("Player gained a life. Total lives: " + playerLives.Lives);
    }
}

{% endhighlight %}

The PlayerLives object is pretty simple and allow our other classes to manage its data at ease:

{% highlight c# linenos %}
using System;

public class PlayerLives
{
    public int Lives { get; set; }

    public void LoseLife()
    {
        if (Lives > 0)
        {
            Lives--;
        }
    }

    public void GainLife()
    {
        if (Lives < 3)
        {
            Lives++;
        }
    }

    public PlayerLives(int lives = 3)
    {
        Lives = lives;
    }
}
{% endhighlight %}

And lastly this is how I'm calling the public methods from `PlayerController`. This section required research to understand the best practices around sharing data between `GameObjects` and `classes` in C#. After exploring various approaches, I implemented this pattern which is commonly used in Unity scripting.

{% highlight c# linenos %}
// ...code
// first we get the reference to playerController from the scene and verify if we were to collect that ref successfully by
// simply verifying if playerController is null or not
void Start() 
{
   playerController = GameObject.FindFirstObjectByType<PlayerController>();
}

// if we have the reference, we should just start leveraging the public methods from playerController
 private void OnTriggerEnter(Collider other)
{
  // This section is an example of I'm handling the projectile and animal collision and
  // what happens once that collision box is triggered. We start by verifying if we are in fact
  // handling the expected game objects by comparing tags, then we destroy the projectile
  // and proceed the assing a life to the player.
  // Whether we destroy the animal gameobject or not is handled in the animal health bar which is 
  // where we are handling the amount
  if (gameObject.CompareTag("Animal") && other.gameObject.CompareTag("Projectile"))
        {
            // start with destroying projectile
            Destroy(other.gameObject);
            playerController.GainLife();
            Debug.Log("Player gained a life.");
            // Check if animalHealthBar is not null before calling AddHealth
            if (animalHealthBar != null)
            {
                animalHealthBar.AddHealth();
            }
            else
            {
                Debug.LogError("AnimalHealthBar is null.");
            }
        }
}
{% endhighlight %}

## The Health Bar

Implementing the health bar on the animals prefab is considered an **_expert_** challenge type. As the final item on the bonus challenge list, it required implementing a visual health system based on provided reference images and videos. This was entirely new territory that required independent research and implementation.

My journey started by exploring the [UI Slider element in Unity's API](https://docs.unity3d.com/Manual/UIE-uxml-element-Slider.html). While the documentation provided useful information about the component itself, it lacked clear instructions on implementing it in a scene.

Next, I explored the UI Builder, which taught me about plotting UI elements, CSS customization, and UI Document management in the hierarchy. Though this knowledge proved valuable, it wasn't quite what I needed for this specific implementation.

Finally, I discovered documentation about displaying sliders in-game. Combined with the official API docs, this allowed me to create a slider prefab and attach it as a child to the animal prefab. See image below.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/prefab-child.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    An image showing the UI Slider prefab as a child of the animal (Doe) prefab.
</div>

> The key point during the position adjustment is to **_reset_** the _**rect transform**_ once brought as a child. That simplifies the process of setting its position in relation to the animal otherwise it get can messy very quickly

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/rect-1.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/rect-2.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Start with the vertical ellipsis button on the right, and then find the option to reset
</div>


Lastly, the implementation of the Animal Health Bar class:

{% highlight c# linenos %}
using UnityEngine;
using UnityEngine.UI;

public class AnimalHealthBar : MonoBehaviour
{
    public Slider healthBar;
    public int amountToBeHealed = 3;
    private int currentAmount = 0;
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        healthBar.fillRect.gameObject.SetActive(true);
        healthBar.minValue = 0;
        healthBar.maxValue = amountToBeHealed;
        healthBar.value = 0;
    }

    // Update is called once per frame
    void Update()
    {

    }

    public void AddHealth()
    {
        currentAmount++;
        healthBar.value = currentAmount;
        if (currentAmount >= amountToBeHealed)
        {
            healthBar.value = 0;
            currentAmount = 0;
            Destroy(gameObject);
            healthBar.fillRect.gameObject.SetActive(false);
        }
    }
}

{% endhighlight %}

For the last step, referencing the slider in the script to close the loop. 

<div class="row justify-content-center">
    <div class="col-7">
        {% include figure.liquid loading="eager" path="assets/img/slider.png"  class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    An image showing the slider prefab added as the health bar public parameter in the script.
</div>

> It's important to notice that I have mixed some of the technical terminology here. AmountToBeHealed should be interpreded as feeding the animals with the sandwhich. Honest mix up :)

And that concludes the working prototype for the animal feeder game. In the github repo, I have a list QOL improvements and features that I'd like to implement in the near future to improve the overall player experience. Thanks for reading!