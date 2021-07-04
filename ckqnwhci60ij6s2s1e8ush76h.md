## Understanding async and defer.

Async and Defer are two boolean attributes for script tag. Both `async` and `defer` increase the speed and performance of web apps by eliminating render-blocking JavaScript.


![normal.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1625323067292/0v--XPz5H.png)
With reference to the above image, consider we simply write `<script>` without `async` or `defer`. Here, while the HTML is parsing, if a script tag is encountered, then the HTML parsing is paused and javascript is fetched. After fetching, the script is executed. During all this time the HTML parsing is paused which may lead to half-loaded webpages or very slow loading. HTML parsing is resumed only after Javascript is executed. The pausing of HTML parsing is known as render-blocking. 

# How can we improve this?

## Async
One of the methods is using the `async` boolean attribute. Take a look at the illustration below:

![async.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1625323434804/6HvWQ9QQB.png)

When we use `async` along with `<script>`, the HTML parsing starts, and whenever `<script>` is encountered, HTML parsing is not paused. Javascript is fetched asynchronously along with HTML parsing. This reduces the loading time of the webpage, boosting its performance. After the script is fetched, only then the HTML parsing is paused and the Javascript is executed. After js execution, the HTML parsing is resumed. 

## Defer
The second boolean attribute is `defer`.

![defer.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1625324328815/aypVrZSAq.png)

When we use `defer`, HTML parsing is never paused. So your entire web page is loaded first. If in the process of parsing HTML, `<script>` is encountered, then is fetched without pausing HTML parsing. After the entire HTML is parsed, the javascript is executed.

### Note:
If there are multiple inter-dependent scripts, say Javascript files, then using `async` won't guarantee the order of execution. But with `defer`, the scripts are executed in the same order as they are called.


![async defer.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1625324655905/k6tWwHYca.png)

To learn more:
 [async vs defer attributes in Javascript](https://www.youtube.com/watch?v=IrHmpdORLu8)


 







