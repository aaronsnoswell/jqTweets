# jqTweets

A simple jQuery plugin to display a twitter feed with images from
pic.twitter.com and Instagram. Output from this library looks very simmilar to
that produced by the Twitter
["Embedded Timelines"](https://dev.twitter.com/docs/embedded-timelines)
feature.

This code is based on the
[excellent tutorial series at Queeness.com](http://www.queness.com/post/8881/create-a-twitter-feed-with-attached-images-from-media-entities)
Image loading code added by me
([Aaron Snoswell](http://twitter.com/aaronsnoswell)), the author.

## Usage

<!-- Freaking MarkDown parsers... -->
<ol>
    <li>
    Include <a href="http://jquery.com/">jQuery</a> and jquery.jqtweets.js to your html file.

    <code><script src="js/jquery.js"></script>
<script src="js/jquery.jqtweets.js"></script>
</code>
    </li>
    <li>
        Create a div where you would like the tweets to show up.

        <code><div id="mytweets" ></div></code>
    </li>
    <li>
        Create a jqTweets object, then load some tweets!

        <code>var tweets = new jqTweet("YourUsername", "#mytweets", 10);

tweets.loadTweets(function() {
    console.log("Got tweets!");
});
</code>

        Tweets will be fetched from the twitter server and stuffed into your div. Any
        images from http://pic.twitter.com/ or http://instagr.am/ will automatically
        be asynchronously fetched and stuffed into the feed as well.

        jqTweet takes 3 paramaters, the username you would like to fetch tweets for
        (without the '@' prefix), the div you would like to place the tweets in (can
        be a css identifier, as in the example above, or an actual element), and the
        number of tweets you would like to fetch.

        You can refresh the twitter feed at any time by calling
        <code>jqTweets.loadTweets</code> again, which takes an optional completion callback. All
        tweet fetching runs asynchronously.
    </li>
    <li>
        (Optional) If you are expecting images from Instagram in your tweet feed,
        add the following css to your page somewhere.

        <code>/* Hide tweet images that haven't been fetched from Instagram yet */
img[src=""] {
    display: none;
}
</code>
    </li>
</ol>

## Twitter API Limits

Note that the
[Twitter API terms of service](https://dev.twitter.com/terms/api-terms) and
[rate limiting](https://dev.twitter.com/docs/rate-limiting) apply to this
library - don't do stupid things and don't try and load tweets from Twitter
more than 150 times per day per IP Address.

It is advised that the user add client-side caching to prevent going over this
limit.

## Markup

The tweet markup is desinged to be minimalistic and easy to style. It looks
kinda like the following;

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


