# Web Takedown: Episode 1

## GetIT

I think you can break it easily, this target doesn’t seem so hard. Can make yourself an admin?

**Target URL:  http://13.251.148.233/FAVCYI1W**

> Hint #1:	Take a closer look at the URL.

### Approach

We noticed that the full URL is actually `http://13.251.148.233/FAVCYI1W/?u=dXNlcg==`, implying a query has been called. Passing it through CyberChef we notice that `dXNlcg==` is base64 for 'user'. 

Therefore, to get admin access, we converted 'admin' to base64, and sent an updated query `http://13.251.148.233/FAVCYI1W/?u=YWRtaW4=`, which gave us the flag.

### Flag

```html
CDDC21{!t_was_aN_EASY0ne}
```

## Hidden Secret

This server looks promising. Can you find the secret?

**Target URL: http://13.251.148.233/P3SLFHDR**

> Hint #1:	Check what files are being sent by the server. You can use the Inspect tool to find the secret file.

### Approach

Using the inspect tool, we notice this line in the HTML:

```html
<script type="text/javascript" src=secret.js></script>
```

Inside `secret.js` we have URL-encoded characters. Decoding them twice and then converting from decimal through Cyberchef, we get the flag.

### Flag

```html
CDDC21{_ De0bfu$cated-F!aG_}
```

## Traversal

I know that this server is vulnerable, but I can’t exploit it. Show your skills and find the right file.

Target URL: http://13.251.148.233/4HOF3DTV

### Approach

Doing a bit of background research on the challenge title, we found that we can exploit the Path Traversal vulnerability in the website through the following:

```html
<div class="nav-bar">
	<img class="logo" src="images/logo.png">
		<a class="active" href=?page=home.php>Home</a>
		<a href=?page=about.php>About</a>
		<a href=?page=serives.php>Services</a>
</div>
```

Executing a GET request from the following URL `http://13.251.148.233/4HOF3DTV/?page=..././..././..././..././..././..././etc/passwd` gives us the flag.

### Flag

```html
CDDC21{!_like_the_PASSWD-F!le!}
```