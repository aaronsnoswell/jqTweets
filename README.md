# jqTweets

A simple jQuery plugin to display a twitter feed with images from
pic.twitter.com and Instagram.

This code is based on the excellent tutorial at Queeness.com. See
http://www.queness.com/post/8881/create-a-twitter-feed-with-attached-images-from-media-entities
Image loading code added by me
((Aaron Snoswell)[http://twitter.com/aaronsnoswell]), the author.

## Usage

1. Include [jQuery](http://jquery.com/) and jquery.jqtweets.js to your html file.

```html
<script src="js/jquery.js"></script>
<script src="js/jquery.jqtweets.js"></script>
```

2. Create a div where you would like the tweets to show up.

```html
<div id="mytweets" ></div>
```

3. Call jqTweets!

```js
var tweets = new jqTweet("YourUsername", "#mytweets", 10);
```

Tweets will be fetched from the twitter server and stuffed into your div. Any
images from http://pic.twitter.com/ or http://instagr.am/ will automatically
be asynchronously fetched and stuffed into the feed as well.

jqTweet takes 3 paramaters, the username you would like to fetch tweets for
(without the '@' prefix), the div you would like to place the tweets in (can
be a css identifier, as in the example above, or an actual element), and the
number of tweets you would like to fetch. The initial fetch of tweets runs
asynchronously.

Note that the Twitter API usage requirements apply to this library - you will
only be able to load tweets from the server 150 times per day per IP Address.

It is advised that the user add client-side caching to prevent going over this
limit.

You can refresh the twitter feed at any time by calling
`jqTweets.loadTweets`, which takes an optional completion callback.

```js
tweets.loadTweets(function() {
    console.log("Got new tweets!");
});
```

4. (Optional) If you are expecting images from Instagram in your tweet feed,
add the following css to your page somewhere.

```css
/* Hide tweet images that haven't been fetched from Instagram yet */
img[src=""] {
    display: none;
}
```

## Markup

The tweet markup is as follows:

```html
<div id="tweets">
    <div class="tweet">Tweet text goes here... Usernames and hashtags will be automatically linkified
        <div class="tweet_media">
            <a ><img /></a>
            <a ><img /></a>
            <!-- ... for each image attached to the tweet -->
        </div>
    </div>
</div>
```

Happy Coding!

