---
creation date: <% tp.file.creation_date() %>
modification date: <% tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") %>
banner: "[[lovley.png]]"
date: <% tp.date.now("YYYY-MM-DD-hh-mm") %>
---

<< [[<% tp.date.now("YYYY-MM-DD", -1) %>]] | [[<% tp.date.now("YYYY-MM-DD", 1) %>]] >>

# <% tp.file.title %>

<% tp.web.daily_quote() %>


// Random picture
<% tp.web.random_picture() %>
// Random picture with size
<% tp.web.random_picture("200x200") %>
// Random picture with size and query
<% tp.web.random_picture("200x200", "landscape,water") %>

<% tp.web.random_picture("200x200", "landscape,cloud") %>


// Simple request <% tp.web.request("https://jsonplaceholder.typicode.com/todos/1") %> // Request with path <% tp.web.request("https://jsonplaceholder.typicode.com/todos", "0.title") %>


<% tp.date.now("YYYY-MM-DD", "P-1M") %>