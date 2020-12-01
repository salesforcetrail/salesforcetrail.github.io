---
title: "About"
layout: single
permalink: /about
author_profile: true


header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/about.jpg
  caption: "Photo credit: [**Unsplash**](https://unsplash.com)"
excerpt: "We are passionated Salesforce developers sharing our findings and experiences. Please don't hesitate to ask me if you have any questions."

---
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-6WR493M663"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-6WR493M663');
</script>
<!-- Global site tag (gtag.js) - Google Analytics -->

## About us
Hi there. We are passionate software developers and Salesforce enthusiast.
## About this blog
In this blog we are going to share our experience about different technologies, mainly Salesforce related ones.
## Contact us
We am always open for discussion, so you are always welcome to left some comments and discuss if you agree or disagree with me.

If you have any other questions, please feel free to contact us:

<form id="my-form"
  action="https://formspree.io/f/mgeplrdr"
  method="POST"
>
  <label>Email:</label>
  <input type="email" name="email" />
  <label>Message:</label>
  <input type="text" name="message" />
  <button id="my-form-button">Submit</button>
  <p id="my-form-status"></p>
</form>

<!-- Place this script at the end of the body tag -->

<script>
  window.addEventListener("DOMContentLoaded", function() {

    // get the form elements defined in your form HTML above
    
    var form = document.getElementById("my-form");
    var button = document.getElementById("my-form-button");
    var status = document.getElementById("my-form-status");

    // Success and Error functions for after the form is submitted
    
    function success() {
      form.reset();
      button.style = "display: none ";
      status.innerHTML = "Thanks!";
    }

    function error() {
      status.innerHTML = "Oops! There was a problem.";
    }

    // handle the form submission event

    form.addEventListener("submit", function(ev) {
      ev.preventDefault();
      var data = new FormData(form);
      ajax(form.method, form.action, data, success, error);
    });
  });
  
  // helper function for sending an AJAX request

  function ajax(method, url, data, success, error) {
    var xhr = new XMLHttpRequest();
    xhr.open(method, url);
    xhr.setRequestHeader("Accept", "application/json");
    xhr.onreadystatechange = function() {
      if (xhr.readyState !== XMLHttpRequest.DONE) return;
      if (xhr.status === 200) {
        success(xhr.response, xhr.responseType);
      } else {
        error(xhr.status, xhr.response, xhr.responseType);
      }
    };
    xhr.send(data);
  }
</script>

[Blog]: /blog

