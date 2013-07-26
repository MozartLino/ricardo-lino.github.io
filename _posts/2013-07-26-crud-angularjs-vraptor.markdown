---
layout: post
title:  "CRUD AngularJs com Vraptor"
date:   2013-07-26 14:52:28
categories: jekyll update
---

Olá pessoal!
Esse post tem o intuito de apenas introduzir o AngularJs com Vraptor e despertar o interesse nesses frameworks.

<p>
Hoje vou tentar mostrar como está cada vez mais fácil e rápida a maneira de criar boas aplicações web. Assim iremos fazer um CRUD utilizando dois frameworks: Vraptor(server-side) e AngularJs(cliente-side)
</p>

<p>
Hoje vou tentar mostrar como está cada vez mais fácil e rápida a maneira de criar boas aplicações web. Assim iremos fazer um CRUD utilizando dois frameworks: Vraptor(server-side) e AngularJs(cliente-side)
</p>

<p>
Muitos desenvolvedores não se sentem à vontade com o famigerado JSP e acabam optando pelo JSF, pois de certa forma alivia nossas preocupações na parte (cliente-side), já que seus componentes prontos deixam seus projetos bem mais produtivos.ddu tentar mostrar como está cada vez mais fácil e rápida a maneira de criar boas aplicações web. Assim iremos fazer um CRUD utilizando dois frameworks: Vraptor(server-side) e AngularJs(cliente-side)
</p>

<p>
No entanto, se você quer criar um site com animações, efeitos, carregamento dinâmico de dados em tempo real etc., o JSF não é uma boa ideia já que a vantagem de se ter componentes prontos te traz alguns pontos negativos, como a perda do controle do seu HTML/CSS e javascript.
</p>

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

