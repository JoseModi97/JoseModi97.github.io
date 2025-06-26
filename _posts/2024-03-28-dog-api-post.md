---
layout: post
title: "Fetching and Displaying Dog Images with the Dog API"
date: 2024-03-28
categories: Fun
tags: [api, javascript, dogs, fun]
---

## Random Dog Pictures!

Who doesn't love a random dog picture? In this post, we'll explore how to use the free [Dog API](https://dog.ceo/dog-api/) to fetch and display adorable dog images on a webpage.

### What is the Dog API?

The Dog API is a simple, free API that provides a collection of dog images. You can fetch images randomly, by breed, or even by sub-breed. For this example, we'll focus on getting a random dog image.

### Let's See Some Dogs!

Here's a simple setup to display a dog image and a button to fetch a new one:

```html
<div style="text-align: center;">
  <h2>Cute Doggo</h2>
  <img id="dogImage" src="" alt="A cute dog" style="max-width: 500px; max-height: 400px; border: 1px solid #ccc; padding: 10px;">
  <br>
  <button id="fetchDogButton" style="margin-top: 15px; padding: 10px 20px; font-size: 16px;">Fetch New Dog!</button>
</div>

<script>
  const dogImageElement = document.getElementById('dogImage');
  const fetchDogButton = document.getElementById('fetchDogButton');

  async function fetchRandomDogImage() {
    try {
      const response = await fetch('https://dog.ceo/api/breeds/image/random');
      if (!response.ok) {
        throw new Error(`HTTP error! status: ${response.status}`);
      }
      const data = await response.json();
      if (data.status === 'success') {
        dogImageElement.src = data.message;
      } else {
        console.error('Failed to fetch dog image:', data.message);
        dogImageElement.alt = 'Failed to load image';
      }
    } catch (error) {
      console.error('Error fetching dog image:', error);
      dogImageElement.alt = 'Error loading image';
    }
  }

  // Fetch an image when the page loads
  fetchRandomDogImage();

  // Add event listener to the button
  fetchDogButton.addEventListener('click', fetchRandomDogImage);
</script>
```

### How it Works

1.  **HTML Structure:**
    *   We have an `<img>` tag with the ID `dogImage` where the fetched dog picture will be displayed.
    *   A `<button>` with the ID `fetchDogButton` will trigger fetching a new image when clicked.

2.  **JavaScript Logic:**
    *   `dogImageElement` and `fetchDogButton`: We get references to our HTML elements.
    *   `fetchRandomDogImage()`: This asynchronous function does the main work:
        *   It uses `fetch()` to make a GET request to the `https://dog.ceo/api/breeds/image/random` endpoint.
        *   It checks if the response was successful.
        *   It parses the JSON response. The API returns an object with a `message` field containing the image URL and a `status` field.
        *   If the status is `success`, it sets the `src` attribute of our `<img>` tag to the fetched image URL.
        *   Error handling is included to catch network issues or API errors.
    *   **Initial Fetch:** We call `fetchRandomDogImage()` once when the script loads to get an initial dog picture.
    *   **Button Event Listener:** We add an event listener to `fetchDogButton` so that `fetchRandomDogImage()` is called every time the button is clicked.

And that's it! Now you have a simple webpage that can display an endless stream of cute dog pictures. You can expand on this by exploring other endpoints of the Dog API, like fetching images by specific breeds. Go ahead and try it out!
