# RippleEffect
A simple way to update multiple elements in the DOM based on user interaction.

### For Example

If we had the following code and wanted to update all of the elements individually, we may decide to find each of the elements or find the parent and traverse the DOM to apply any changes. But this can lead to hard to manage code. If we decided to change the layout of this code in the future we would also need to update the traversed selectors and/or class names.

```html
<div class="container">
   <div class="user-panel">
        <div class="user-panel__img"></div>
        <h1 class="user-panel__name">Lorem Ipsum</h1>
        <p class="user-panel__intro">
            Lorem ipsum dolor sit, amet consectetur adipisicing elit. Minus veniam, aut et numquam at 
            quas soluta beatae repellat temporibus error quae delectus
        </p>
        <button class="btn btn--clear">get started</button>
   </div>
</div>
```

By simply adding a class to the parent element, this task can be much easier.

When the parent element here has an active modifier applied, various styles on the child elements are also updated.

```scss
.user-panel{
    //Main styles would go here...

    //styles to be applied when the parent element also has an active modifier applied
    &--active{
        &::after{
            transform: scale(50);
        }

        .btn{
            display: none;
        }

        & .user-panel__img{
            width: 120px;
            height: 120px;
            visibility: visible;
        }

        & .user-panel__intro,
        & .user-panel__name{
            transform: translateY(0);
            visibility: visible;
        }
    }
}
```
The key benefit of applying these styles in CSS is that we can change the layout, remove elements or even add more to this section without causing any problems to the code we have already written.


Now all we have to do is add an event listener to apply these changes. For this example I am using a click event.

```js
document.querySelector('.btn').addEventListener('click', function(){
   document.querySelector('.user-panel').classList.add('user-panel--active');
});
```

### The styles above are only applied when the parent has this active modifier they don't effect the page until they are needed.

If you would like to see this simple example in action you can view it on my CodePen here: https://codepen.io/Brett-Owen/pen/MZZbeZ
