<h1>Vue.js Shopping Cart</h1>
<p>This project includes many functionalities on vue.js. I have used <b>methods, lifecycles and props.</b></p>
<p>Styling wasn't considered as an objective in this project. I used simple grid with three columns. Users are expected to inspect page on desktop devices</p>
<h3>*************</h3>
<p>This project is developed online on <a href="https://codesandbox.io">Codesandbox.io</a>. You are able to see project working online <a href="https://ui9re.csb.app/"> in this link</a> and codes <a href="https://codesandbox.io/s/nervous-mestorf-ui9re?">on this link</a> but you can still go with old school with downloading and running on local machine :smirk:</p>
<h3>*************</h3>
<h2>Functionalities</h2>
<h3>Preloader</h3>
<p>Since user experience is very important on these days, I have added an preloader with a simple way. <b>V-IF</b> tags provides us an easy way to show or hidden elements also knows as conditional rendering. I have selected a stylish GIF from website. This GIF is visible while our application is still fetching data and loading them to our objects.</p>
<h3>Fetch from api</h3>
<h5>API documentation can be found at <a href="https://github.com/keikaavousi/fake-store-api">Fake Store API Github</a>. Don't forget to drop a star on their repo :star:</h5>
<p>I have used an great API named <a href="https://fakestoreapi.com" target="_blank">fakestoreapi</a> that provides some products for free. As it can be seen on  <a href="https://vuejs.org/v2/api/#mounted">Vue's offical documentation of lifecycles</a>, I have used mounted hook to fetch api and set values to my own object. After fetch operation we are setting our loading state to done which effects our application to hide preloader and show our products.</p>
<h3>Add to cart</h3>
<p>Assuming this page as a shop, it is definitely needed to add a cart functionality to shop page. I have added a button with a text for every product that triggers one of our methods on click. This method moves our clicked item from product array to cart array and increases our cart item value by one.</p>
<h3>Show cart</h3>
<p>I have used a floating button as we can see on top right of our page. This button shows our cart on click event but also shows how many items are in our cart while not clicked. Clicking to button changes our <b>V-IF</b> state to show our floating cart list. In cart screen we are able to see items that we have added with their name and prices. In the bottom right corner we are able to see total price of our cart</p>
