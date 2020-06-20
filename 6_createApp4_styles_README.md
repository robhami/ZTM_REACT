## Styling App ##

### Index.css ###
In index.css, set background gradient using background generator:

```
body {
  margin: 0;
  padding: 0;
  font-family: san-serif;
  background: linear-gradient(to left, rgb(0, 255, 51), rgb(81, 0, 255));
  
}
```

### Create App.css ###

Create App.css in src folder. 

Get SEGA font from: 

https://www.cufonfonts.com/font/sega-logo-font\

Download it. Put .woff file in src folder. Then copy the css file's text and paste into App.css and add h1 styling:

```
@font-face {
font-family: 'SEGA LOGO FONT';
font-style: normal;
font-weight: normal;
src: local('SEGA LOGO FONT'), url('SEGA.woff') format('woff');
}

h1 {
	font-family: "SEGA LOGO FONT";
}
```

### Import to App.js ###

Add to App.js: 

```
import './App.css';
```
