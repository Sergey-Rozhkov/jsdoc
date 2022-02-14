# Questions

Vue js comes with following features Templates Reactivity Components Transitions Routing

//-----------------------------------------------------------------------------

What is virtual dom in Vuejs?

Virtual DOM in Vue is a JavaScript object that represents the Document Object Model (DOM). The application updates the Virtual DOM instead of the DOM directly. So, it minimizes the updating cost of the real DOM as it is computationally expensive. Virtual DOM offers the ability to control the timing at which the Virtual DOM is rendered. Virtual DOM will just maintain the state of the data without re-rendering until you choose it. Virtual DOM also offers the ability to optimize the performance of your web applications by minimizing the number of times the DOM has to be updated.

//-----------------------------------------------------------------------------

Назовите хуки жизненного цикла компонента в Vue.js? https://ru.vuejs.org/images/lifecycle.png

//-----------------------------------------------------------------------------

How to create a component in Vue js? Components in Vue JS are a single, independent unit of an interface. They have their own state, markup, and style. A Vue component can be defined in four ways. The first is new Vue({ /\*options _/ }). The second is Vue.component(‘component-name’, { /_ options \*/ }). The third way is by using the local components. The fourth is in the .vue files or Single File Components. The first two ways are the standard ways to use Vue when building an application that is not a SPA (Single Page Application). The Single File Components are uses in the Single Page Application.

//-----------------------------------------------------------------------------

Как передать данные компоненту? Существует два способа: с помощью атрибут(props) или через события.

Когда вам нужно передать данные после какого-то определенного события, вы должны использовать диспетчеров и вещателей.

Для отправки события из двух дочерних компонентов используйте следующий синтаксис

this.$dispatch('something\_happen', data); // Event listenerevents: { 'something\_happen': function(data) { // Handle event } }

//-----------------------------------------------------------------------------

data binding

In one-way data flow the view(UI) part of application does not updates automatically when data Model is change we need to write some custom code to make it updated every time a data model is changed. In Vue js v-bind is used for one-way data flow or binding.

In two-way data binding the view(UI) part of application automatically updates when data Model is changed. In Vue.js v-model directive is used for two way data binding.

//-----------------------------------------------------------------------------

Что такое вычисляемые свойства и когда их нужно использовать?

//-----------------------------------------------------------------------------

Что такое Vuex ?

//-----------------------------------------------------------------------------

What are Directives in VUE.js, List some of them you used?

The concept of directive in Vue js is drastically simpler than that in Angular. Vue.js directives provides a way to extend HTML with new attributes and tags. Vue.js has a set of built-in directives which offers extended functionality to your applications.You can also write your custom directives in Vue.js . Below are list of commonly used directives in Vue.js v-show v-if v-model v-bind v-else v-on

In Vue js following types of directives are available General Directives Literal Directives Empty Directives Custom Directives //-----------------------------------------------------------------------------

Как сделать условный рендеринг компонента?

Используйте директивы v-if и v-else, компонент будет удален из dom, если вы передадите ему ложное условие. Для сохранения элемента в директиве DOM v-show может быть использовано css свойство display/

//-----------------------------------------------------------------------------

Как защитить какой-то маршрут от несанкционированного доступа?

Его можно сделать внутри компонента или в глобальных guards. const router = new VueRouter({ ... }) router.beforeEach((to, from, next) => { if (to.isProtected() && !haveAccess(user)) { next(false) } next() })

//-----------------------------------------------------------------------------

Примеси (mixins) https://ru.vuejs.org/v2/guide/mixins.html

//-----------------------------------------------------------------------------

Фильтры https://ru.vuejs.org/v2/guide/filters.html
