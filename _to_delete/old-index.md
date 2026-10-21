---
layout: base
title: Student Home 
description: Home Page
hide: true
---

<style>
    /* Style for the dropdown container */
    .dropdown {
        position: relative;
        display: inline-block;
    }

    /* Style for the dropdown button */
    .dropdown-button {
        background-color: #00f5ff;
        color: white;
        padding: 10px 20px;
        font-size: 16px;
        border: none;
        cursor: pointer;
        border-radius: 5px;
    }

    /* Dropdown menu container */
    .dropdown-content {
        display: none;
        position: absolute;
        background-color: #f9f9f9;
        min-width: 200px;
        box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
        z-index: 1;
        border-radius: 5px;
        margin-top: 5px; /* Adjust for better placement */
    }

    /* Dropdown menu items */
    .dropdown-content a {
        color: black;
        padding: 12px 16px;
        text-decoration: none;
        display: block;
        border-radius: 5px;
    }

    /* Change color on hover */
    .dropdown-content a:hover {
        background-color: #ddd;
    }

    /* Show the dropdown menu on hover */
    .dropdown:hover .dropdown-content {
        display: block;
    }

    /* Style for the dropdown button when menu is shown */
    .dropdown:hover .dropdown-button {
        background-color: #00aaff;
    }
</style>

<div class="dropdown">
    <button class="dropdown-button">Personal Projects</button>
    <div class="dropdown-content">
        <a href="{{site.baseurl}}/game">Play My Game</a>
        <a href="{{site.baseurl}}/devops/python">One Fruit codes</a>
        <!-- Add more links as needed -->
    </div>
</div>

My journey starts here.
