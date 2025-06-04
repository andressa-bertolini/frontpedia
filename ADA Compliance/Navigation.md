Navigation Menu Markup

```
<nav aria-label="main">
  <ul>
    <li>
      <button aria-expanded="false" aria-controls="shop-menu">
        Shop
      </button>
      <div id="shop-menu">
        <ul>
          <li><a href="#">Link 1</a></li>
          <li><a href="#">Link 2</a></li>
          <li><a href="#">Link 3</a></li>
          <!-- Etc. -->
        </ul>
      </div>
    </li>
    <li>
      <button aria-expanded="false" aria-controls="about">
        About
      </button>
      <!-- About menu -->
    </li>
  </ul>
</nav>
```