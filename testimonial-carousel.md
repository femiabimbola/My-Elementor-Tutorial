# Testimonial Carousel

### Creating two containers

- One for the testimonial
- The second for the codes

### The first container (_testimonial_)

Create two sub division container for the testimonial. One to contain the images, the other to contain the testimonial text.

For each of the images, put **tabmenu** in the css classes then in the attributes put **data-tab|1** in the attribute section, the <b>1</b> should be **2** or irrespective of the image. Put **active** in the first image CSS so it becomes **tabmenu active**

In the each of the container having the testimonial, put **text-details active** in the css classes and put **text-1** in the CSS ID. The respective id for the other testimonial will be **text-2** and the active will be removed.

Then in the container house both contianers, go to the advanced css section and place the following code

```css
selector .tabmenu {
  opacity: 0.2;
  cursor: pointer;
  transition: opacity 0.3s ease, transform 0.3s ease;
  transform: scale(1); /* Ensure a baseline scale for smooth transitions */
}

selector .tabmenu.active {
  opacity: 1;
  transform: scale(1.2);
}

@media (max-width: 768px) {
  .tabmenu {
    /* You can reset the styles or simply override them */
    display: none;
  }

  .tabmenu.active {
    /* You may need to reset the active state styles as well */
    display: block;
    opacity: 1;
    transform: none;
  }
}
```

### The second container

Create the second container, and put the html widget on it. Then past the following code

```js
<script>
    document.addEventListener('DOMContentLoaded', function() {

    // Initial setup
    const textDetails = document.querySelectorAll('.text-details');
    const tabItems = document.querySelectorAll('.tabmenu');
    let currentIndex = 0;

    textDetails.forEach(detail => {
        if (!detail.classList.contains('active')) {
            detail.style.display = 'none';
        }
    });

    // Function to activate a specific tab
    function activateTab(index) {
        const currentTab = tabItems[index];
        const dataId = currentTab.getAttribute('data-tab');

        // Text transition
        const activeTextDetail = document.querySelector('.text-details.active');
        const nextTextDetail = document.getElementById('text-' + dataId);

        if (activeTextDetail) {
            activeTextDetail.classList.remove('active');
            activeTextDetail.style.transition = 'opacity 0.3s ease-in-out';
            activeTextDetail.style.opacity = 0;

            setTimeout(() => {
                activeTextDetail.style.display = 'none';
                nextTextDetail.style.display = 'block';
                nextTextDetail.classList.add('active');
                nextTextDetail.style.transition = 'opacity 0.3s ease-in-out';
                nextTextDetail.style.opacity = 1;
            }, 300);
        } else {
            nextTextDetail.style.display = 'block';
            nextTextDetail.classList.add('active');
            nextTextDetail.style.opacity = 1;
        }

        // Tab styling
        tabItems.forEach(tab => {
            tab.classList.remove('active');
        });
        currentTab.classList.add('active');
    }

    // Manual click handler
    tabItems.forEach((tab, index) => {
        tab.addEventListener('click', function() {
            currentIndex = index;
            activateTab(currentIndex);
        });
    });

    // Auto-carousel function
    setInterval(() => {
        currentIndex = (currentIndex + 1) % tabItems.length;
        activateTab(currentIndex);
    }, 4000); // change every 4 seconds

});
</script>
```
