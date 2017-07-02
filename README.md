comment.js
===

Pure JavaScript to make a Disqus-like comment system. Use issue system of code hosting sites like Github/OSChina as the backend. Easily to use. Free for running.

## Demo

* [Demo Comment Thread](http://wzpan.github.io/comment.js#comment-thread)
* [Demo Recent Comment List](http://wzpan.github.io/comment.js#recent-comments)

## Dependencies

* [jQuery](https://jquery.com/) - for making Ajax requests and manipulating DOM.
* [markdown-js](https://github.com/evilstreak/markdown-js) - for rendering markdown.
* [timeago.js](https://github.com/hustcc/timeago.js) - for formatting time labels.
* [spin](https://github.com/fgnass/spin.js) - for displaying a spinning indicator(optional).

## How to use

### 0. Add stylesheets and JavaScript files

``` html
<!-- stylesheet -->
<link rel="stylesheet" href="path_to_comment_css/comment.css">

<!-- javascripts -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.js">/script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/markdown.js/0.5.0/markdown.min.js">/script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/timeago.js/3.0.2/timeago.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/spin.js/2.3.2/spin.min.js"></script>
<script src="path_to_comment_js/comment.js"></script>
```

### 1. Create Github Repo

Create a Github repo for hosting your comments.

### 2. Register an OAuth App

To avoid abused API calling, Github API (and the same as OSChina API) has [Rate Limiting](https://developer.github.com/v3/#rate-limiting). To enlarge the limit you can [Register a OAuth application](https://github.com/settings/applications/new) . 

After that, you will get a client id as well as a client secret.

(Tips: When you registeing the App, the Authorization callback URL can be assigned as your site address. For example http://hahack.com )

### 3. Comment Thread

In this section I will describe on how to generate a comment thread for a certain page for your site.

Firstly, Write a div for placing your comment thread.

``` html
<div id="comment-thread"></div>
```

Secondly, write a div for placing a spinning indicator(optional):

``` html
<div id="loading-spin"></div>
```

Thirdly, call `getComments()` function to fetch comment thread and display them to the page.

``` js
<script type="text/javascript">
   var opt = {
       type: "github",
	   user: "wzpan",
	   repo: "comment.js",
	   no_comment: "No comments yet. Press the button and go to comment now!",
	   go_to_comment: "Go to comment",
	   issue_id: "1",
	   btn_class: "btn",
	   comments_target: "#comment-thread",
	   loading_target: "#loading-spin",
	   client_id: "xxxxxx",
	   client_secret: "xxxxxx"
   };
   getComments(opt);
</script>
```

parameters explaning:

* `type`: the site as the backend. Currently supports Github and OSChina.
* `user`: your site's user account.
* `repo`: your repo for comment issue tracking.
* `no_comment`: tips when no comments are fetched.
* `go_to_comment`: text of the "go to comment" button.
* `issue_title`: the corresponding issue title to your page. Alternatively you can use `issue_id`. 
* `issue_id`: the corresponding issue id to your page. Alternatively you can use `issue_title`.
* `btn_class`: css class name for the "go to comment" button.
* `comments_target`: target for displaying comment thread. 
* `loading_target`(optional): target for displaying loading a spinning indicator.
* `client_id`(optional but recommended): the client id of your OAuth App.
* `client_secret`(optional but recommended): the client secret of your OAuth App.

example:

<div id="comment-thread"></div>
<div id="loading-spin"></div>
<div style="height:120px"></div>

### 4. Recent Comment List

In this section I will describe on how to generate a recent comment list for your site.

Firstly, Write a div for placing the recent comment list.

``` html
<div id="recent-comments"></div>
```

Secondly, call `getRecentCommentsList()` function to fetch a comment list and display them to the page.

``` js
<script type="text/javascript">
   var opt = {
       type: "github",
	   user: "wzpan",
	   repo: "comment.js",
	   recent_comments_target: "#recent-comments",
	   count: 5,
	   client_id: "xxxxxx",
	   client_secret: "xxxxxx"
   };
   getRecentCommentsList(opt);
</script>
```

parameters explaning:

* `type`: the site as the backend. Currently supports Github and OSChina.
* `user`: your site's user account.
* `repo`: your repo for comment issue tracking.
* `recent_comments_target`: target for displaying recent comment list.
* `count`: the maximize length of the comment list.
* `client_id`(optional but recommended): the client id of your OAuth App.
* `client_secret`(optional but recommended): the client secret of your OAuth App.

example:

<div id="recent-comments"></div>
<div style="height:120px"></div>


