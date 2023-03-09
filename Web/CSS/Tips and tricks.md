## How to find overflowing elements

```
document.querySelectorAll("*").forEach(el => {
  if(el.offsetWidth > document.documentElement.offsetWidth) {
    console.log(el);
  }
})
```
