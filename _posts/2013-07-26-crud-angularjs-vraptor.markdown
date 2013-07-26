---
layout: post
title:  "CRUD AngularJs com Vraptor"
date:   2013-07-26 14:52:28
categories: jekyll update
---
<p>
Olá pessoal!
Esse post tem o intuito de apenas introduzir o AngularJs com Vraptor e despertar o interesse nesses frameworks.

Hoje vou tentar mostrar como está cada vez mais fácil e rápida a maneira de criar boas aplicações web. Assim iremos fazer um CRUD utilizando dois frameworks: Vraptor(server-side) e AngularJs(cliente-side)

<p>
Muitos desenvolvedores não se sentem à vontade com o famigerado JSP e acabam optando pelo JSF, pois de certa forma alivia nossas preocupações na parte (cliente-side), já que seus componentes prontos deixam seus projetos bem mais produtivos.ddu tentar mostrar como está cada vez mais fácil e rápida a maneira de criar boas aplicações web. Assim iremos fazer um CRUD utilizando dois frameworks: Vraptor(server-side) e AngularJs(cliente-side)

<p>
No entanto, se você quer criar um site com animações, efeitos, carregamento dinâmico de dados em tempo real etc., o JSF não é uma boa ideia já que a vantagem de se ter componentes prontos te traz alguns pontos negativos, como a perda do controle do seu HTML/CSS e javascript.


Mesmo com bibliotecas como Jquery, manipular o DOM ainda é trabalhoso. Desenvolvedores, ao perceberem a baixa produtividade de se criar elementos dinamicamente, resolveram criar frameworks para aliviar esse trabalho árduo. Um deles é o AngularJs, que usa o conceito de data-binding, no qual o DOM está ligado diretamente ao modelo.

Sem mais delongas, vou mostrar o primeiro passo para a criação do nosso projeto.
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

<p>
Esse html, não é um html comum, já que na tag html estamos informando através da propriedade ng-app que o AngularJs vai controlá-lo daquele ponto em diante, ou seja, a partir daquele ponto o meu html vira um aplicativo Angular.
A próxima tag ng-controller vai informar ao Angular qual function ele vai usar para aquele escopo, no caso do exemplo, é a function “userController”, Agora perceba que no nosso formulário há campos para o cadastro de usuário e com a tag ng-model estamos ligando os campos ao nosso modelo, assim na function userController podemos manipular esse “model”, ou seja, as alterações feitas na function “userController” reflete nos inputs e vice-versa.
Assim, para manipularmos esse objeto dentro do js, basta acessá-lo através do atributo $scope e manipulá-lo de qualquer forma, um exemplo: salvar esse objeto no banco.
</p>


{% highlight javascript %}
$scope.postUser = function () {
    $http.post('/angularJs/users', user).success(function(data){
        $scope.users.unshift(data);
        reset();
    });
};
 
var reset = function(){
    $scope.user = {id : 0, login : "", name : "", password: ""};
};
{% endhighlight %}


<p>
Perceba que no botão “Send user” do nosso user.html estamos passando qual função ele executará ao ser clicado(que é function “postUser()”). Nela podemos enviar o objeto para o servidor no formato json. E depois jogar para um lista de users, e no final limpar o form com a função reset(). Agora devemos ligar a lista de users ao nosso html. Então vamos acrescentar uma tabela com os usuários já cadastrados no nosso user.html!
</p>

{% highlight html %}
<html ng-app>
<body ng-controller="userController" style="margin-left: 20px">
<h2>User</h2>
	<div>
		<form class="form">
			<input type="hidden" value="" ng-model="user.id">
			<input type="text" ng-model="user.login">
			<input type="text" ng-model="user.name">
			<input type="password" ng-model="user.password">
 
			<button ng-click="postUser()">Send user</button>
			<button ng-click="putUser()" disabled="disabled">Edit user</button>
		</form>
		<table>
			<thead>
				<tr>
					<th>Id</th>
					<th>Login</th>
					<th>Name</th>
					<th>Options</th>
				</tr>
			</thead>
			<tbody>
				<tr ng-repeat="user in users">
					<td>{{user.id}}</td>
					<td>{{user.login}}</td>
					<td>{{user.name}}</td>
					<td>
					     <a href="#" ng-click="edit(user)">
	                  		          <span class="label">edit</span>
	                  	             </a> |
	                  	             <a href="#" ng-click="deleteUser(user)">
	                  		          <span class="label label-important">remover</span>
	                  	             </a>	
					</td>
				</tr>
			</tbody>
		</table>
	</div>
</body>
<script type="text/javascript" src="js/jquery-min.js"></script>
<script type="text/javascript" src="js/angular.min.js"></script>
<script type="text/javascript" src="js/userController.js"></script>
{% endhighlight %}

Essa propriedade funciona como se fosse a tag c:forEach da biblioteca JSTL
Aqui ele liga a lista de user ao elemento tr da tabela, ou seja, quando adicionamos um usuário ele cria um elemento tr, e quando removemos ele exclui o elemento tr vinculado àquele usuário da tabela.
Ao adicionarmos um usuário, o angular automaticamente adicionará esse usuário à lista, isso sem precisar criar qualquer elemento html. Logo o trabalho de criação desses elementos fica por conta do dele.
Podemos também criar as funções para editar o usuário.

{% highlight html %}
ng-repeat="user in users";
{% endhighlight %}
