+++
title = "Contact Vincent Hong"
description = "Contact information of Vincent Hong"
date = 2020-09-27
draft = false
toc = false
+++

<style>
    /* Style inputs with type="text", select elements and textareas */
    input[type=text], select, textarea, input[type=email] {
    width: 100%; /* Full width */
    padding: 12px; /* Some padding */ 
    border: 1px solid #ccc; /* Gray border */
    border-radius: 4px; /* Rounded borders */
    box-sizing: border-box; /* Make sure that padding and width stays in place */
    margin-top: 6px; /* Add a top margin */
    margin-bottom: 16px; /* Bottom margin */
    resize: vertical /* Allow the user to vertically resize the textarea (not horizontally) */
    }

    /* Style the submit button with a specific background color etc */
    input[type=submit] {
    background-color: #2980b9;
    color: white;
    padding: 12px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    }

    /* When moving the mouse over the submit button, add a darker green color */
    input[type=submit]:hover {
    background-color: #3498db;
    }

    /* Add a background color and some padding around the form */
    .container {
    border-radius: 5px;
    background-color: #0a3d62;
    padding: 20px;
    }

    .hidden {
        
        display: none;
    }
</style>

<div class="container">
<form name="contact" action="/thank-you/" data-netlify-recaptcha="true" netlify-honeypot="bot-field" method="POST" netlify>

<p class="hidden">
    <label>Don’t fill this out if you're human: <input name="bot-field" /></label>
</p>

<label for="fname">First Name</label>
<input type="text" id="fname" name="firstname" placeholder="Your name.." required>

<label for="lname">Last Name</label>
<input type="text" id="lname" name="lastname" placeholder="Your last name.." required>

<label for="email">Email</label>
<input type="email" id="email" name="email" placeholder="Your email address.." required>


<label for="message">Message</label>
<textarea id="message-contact" name="message" placeholder="Write your message" style="height:350px"></textarea>

<div data-netlify-recaptcha="true"></div>

<input type="submit" value="Submit">

</form>
</div>

