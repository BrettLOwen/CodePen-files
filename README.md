# RippleEffect
A simple way to update multiple elements in the DOM based on user interaction.

### For Example

If we had the following code and want to update all of these elements individually, most may find each elements or the parent and traverse the DOM to apply any changes. But this can lead to hard to manage code. If we decided to change the layout of this code in the future we would also need to update the 'traversed selectors' or class names etc.

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

Using the RippleEffect way, this task can be much easier.

Let's say we want to change the layout and also animate each element to show them to the user.

```scss
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

        & .user-panel__name{
            transform: translateY(0);
            visibility: visible;
        }

        & .user-panel__intro{
            transform: translateY(0);
            visibility: visible;
        }
    }

```
