---
layout: post
title:  "CRUD AngularJs com Vraptor"
date:   2013-07-26 14:52:28
categories: jekyll update
---

Olá pessoal!
Esse post tem o intuito de apenas introduzir o AngularJs com Vraptor e despertar o interesse nesses frameworks.

{% highlight html %}
<html ng-app>
<body ng-controller="userController">
<h2>User</h2>
    <div>
        <form class="form">
            <input type="hidden" value="" ng-model="user.id">
            <input type="text" ng-model="user.login">
            <input type="text" ng-model="user.name">
            <input type="password" ng-model="user.password">
 
            <button ng-click="postUser()">Save user</button>
            <button ng-click="putUser()" disabled="disabled">Edit user</button>
        </form>
    </div>
</body>
<script type="text/javascript" src="js/jquery-min.js"></script>
<script type="text/javascript" src="js/angular.min.js"></script>
<script type="text/javascript" src="js/userController.js"></script>
</html>
{% endhighlight %}

