### khan_2

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Animating DOM with setInterval</title>
    </head>
    <body>
    <div>
        <img id="ohnoes" src="https://www.kasandbox.org/programming-images/creatures/OhNoes.png">
        <h1>Oh noes, the world will end in
            <span id="countdown">5</span>
            seconds!
        </h1>
    </div>
    
  <script>
  // Step 1. What element do we want to animate?
  var countdown = document.getElementById("countdown");
  // Step 2. What function will change it each time?
  var countItDown = function() {
    var currentTime = parseFloat(countdown.textContent);
    if (currentTime > 0) {
       countdown.textContent = currentTime - 1;   
    } else {
        window.clearInterval(timer);
    }
    
  };
  // Step 3: Call that on an interval
  var timer = window.setInterval(countItDown, 1000);
  </script>

    </body>
</html>
```

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Challenge: Stopwatch</title>
    </head>
    <body>
        
        <button id="stop-button" type="button">Stop</button>
        <p>
            <span id="seconds">0</span> seconds have gone by!
        </p>
        <script>
            // Make it count up on a timer, calling this function
            var seconds = document.getElementById("seconds");
            var countUp = function() {
              var currentTime = parseInt(seconds.textContent);
              seconds.textContent = currentTime + 1;
            };
            var timer = window.setInterval(countUp, 1000);
            // How can you make it stop counting?
            var stopCountUp = function() {
              window.clearInterval(timer);
            };
            var stopButton = document.getElementById("stop-button");          
            stopButton.addEventListener("click", stopCountUp);
            
        </script>
    </body>
</html>
```

> parseInt(seconds.textContent) + 1
>
> var timer = window.setInterval(countUp, 1000)
>
> window.clearInterval(timer)

