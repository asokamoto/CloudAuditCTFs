---
layout: post
title: "Intro Level"
date: 2021-05-28 00:00:04
categories: Levels
comments: false
---

# Intro Level

<details>
	<summary><b>Hint 1</b></summary>
	<p> </p>
	<p>The Google Cloud platform automatically logs many events that take place on the cloud system. To view events related to the leaked key, we can open the log explorer at the url here:</p> 
	<pre><code>https://console.cloud.google.com/logs/query?q=search&referrer=search&project=[ProjectName]</code></pre>
	<p> </p>
</details>

<details>
	<summary><b>Hint 2</b></summary>
	<p> </p>
	<p>The key we are concerned about is stored in the start directory of the console. Navigate there and view the contents of “intro-leaked.json” by entering ‘cat start/intro-leaked.json’ in the cloud shell.</p>
	<p>Near the top there should be a line that looks something like this: </p>
	<pre><code>"private_key_id": "4bc0bf03d99620a3ba9e6c016ec27705b55ef6f5"</code></pre>
	<p> </p>
	<p>This private key ID will be associated with any logs for events performed using the leaked key for authorization.</p>
</details>

<details>
	<summary><b>Hint 3</b></summary>
	<p> </p>
	<p>The query builder at the top of the log explorer is a very useful tool for navigating the logs of a cloud system. To view the logs associated with the leaked key, simply enter the private key ID into the query builder and run the query. </p>
	<p> </p>
</details>

<details>
	<summary><b>Hint 4</b></summary>
	<p> </p>
	<p>The results should be the logs for two events. Notice that the first event has the tag</p>
	<pre><code>CreateServiceAccountKey</code></pre>
	<p> </p>
	<p>this is from when the key was initially generated during the system’s deployment. The second event has the tag</p>
	<pre><code>storage.buckets.get</code></pre>
	<p> </p>
	<p>which is the kind of activity we’re looking for concerning the leaked key. Click on this log and expand the nested fields using the button on the top right of the log.</p>
	<p> </p>
</details>

<details>
	<summary><b>Hint 5</b></summary>
	<p> </p>
	<p>Under “Authentication info" you can find the</p>
	<pre><code>serviceAccountKeyName</code></pre>
	<p> </p>
	<p>field. This field holds the unique identifier for any service account using the leaked key to authenticate actions, which is why we are able to run a query on the leaked key to find these logs. The field should look like this:</p>
	<pre><code>serviceAccountKeyName: 
	"//iam.googleapis.com/projects/thunder-305703/serviceAccounts/intro-npc@[ProjectName].iam.gserviceaccount.com/keys/[PrivateKeyID]"</code></pre>
	<p> </p>
</details>
<details>
	<summary><b>Hint 6</b></summary>
	<p> </p>
	<p>We have found the key name for the service account using the leaked key now, but we have also been tasked with figuring out what data has been accessed with the leaked key. We’re already looking at the correct log, so we can examine it to find the name of the bucket accessed. Unfortunately, the logs do not tell us the name of the file accessed, only which bucket was storing the file. Even so, we know that any data stored in this bucket is potentially compromised, while data in other buckets is still secure for the time being.</p>
	<p> </p>
</details>
	




