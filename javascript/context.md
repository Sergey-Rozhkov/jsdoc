# Context

```javascript
const guitarStore = function() {
    this.guitarCount = 2;

    (function() {
        console.log(`IIFE`, this.guitarCount);
        this.guitarCount = 1;
    })();

    console.log(`guitarCount`, this.guitarCount);
}

const guitarShop = {
    guitarCount: 3,
    showMeAnswer: function () {
        console.log(this.guitarCount);
    }
}

guitarStore();
new guitarStore();
guitarShop.showMeAnswer();
new guitarShop.showMeAnswer();
guitarStore.apply(guitarStore);
guitarShop.showMeAnswer.apply(guitarStore);
guitarStore.bind({})();
```

