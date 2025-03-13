---
layout: post
title: Sandwich projectiles are flying off the screen
date: 2025-03-12 08:00:00
description: Controlling the player and shooting projectiles
tags: career devlog videos
categories: journal
thumbnail: assets/img/unity.png
---


<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/prototype-sandwhich.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
<div class="caption">
    A demonstration of my player shooting sandwhiches off of their position showcasing what a few `transforms` can do.
</div>

I'm currently working my way through the `Programming Pathways in Unity` and have been able to _quickly_ create working prototypes, adding a little of my own flavor to each exercise and challenge.

Thanks to my engineering career and familiarity with other languages, picking up C# has been a very pleasant experience so far. One of the highlights today (besides being able to create all these working, interactable game objects you see in the video) was learning how to use [`Mathf.Clamp`](https://docs.unity3d.com/ScriptReference/Mathf.Clamp.html) to optimize and clean up my code. It’s very useful for limiting a value between minimum and maximum boundaries without having to repeat transform statements in `two` different if statements.

Here's the code for that C# Player Component Script:

{% highlight c# linenos %}
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    public float horizontalInput;
    private float speed = 10.0f;
    private float xRange = 19.0f;
    public GameObject projectilePrefab;
    private float fireRate = 0.25f;
    private float nextFire = 0.0f;
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {

    }

    // Update is called once per frame
    void Update()
    {
        horizontalInput = Input.GetAxis("Horizontal");
        transform.Translate(Vector3.right * horizontalInput * Time.deltaTime * speed);

        // if value on X axis is beyond the minimyum or maximum
        // we clamp to set a stopper value that makes sure the
        // player does not go beyond the set value
        if (transform.position.x < -xRange || transform.position.x > xRange)
        {
            float clampedX = Mathf.Clamp(transform.position.x, -xRange, xRange);
            transform.position = new Vector3(clampedX, transform.position.y, transform.position.z);
        }

        // if the player presses space, we instantiate a new projectile
        // at the player's position and rotation so it moves forward
        if (Input.GetKey(KeyCode.Space) && Time.time > nextFire)
        {
            Instantiate(projectilePrefab, transform.position, projectilePrefab.transform.rotation);
            nextFire = Time.time + fireRate;
        }
    }
}

{% endhighlight %}

I thought of two additional features that I wanted to implement as nice-to-haves to this prototype:

> 1. I wanted to shoot multiple projectiles if the player keeps the key pressed down
> 2. I wanted to implement a fire rate process to avoid shooting projectiles on top of each other, allowing the player to tell when each projectile is being shot (similar concept to throttling api requests)

Once implemented, each sandwich moves through the space as expected, and the player can easily tell when their projectiles are being fired. This results in a much improved user experience.

o7