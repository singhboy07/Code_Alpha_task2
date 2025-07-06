// index.html

<!DOCTYPE html>

<html>

<head><title>Mini Social</title></head>

<body>

 <h1>Posts</h1>

 <div id="posts"></div>

 <script src="script.js"></script>

</body>

</html>

// script.js

fetch('/api/posts')

 .then(res => res.json())

 .then(posts => {

 const div = document.getElementById('posts');

 posts.forEach(p => {

 div.innerHTML += `<div><b>${p.user}</b>: ${p.content}</div>`;

 });

 });

// server.js

const express = require('express');

const app = express();

const posts = [

 { user: 'Alice', content: 'Hello World!' },

 { user: 'Bob', content: 'Nice to meet you' }

];

app.get('/api/posts', (req, res) => {

 res.json(posts);

});

app.listen(3001, () => console.log('Social server on port 3001'));
