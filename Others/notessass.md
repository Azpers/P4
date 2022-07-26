-mixins store groups of styles that you can use over and over again.
-@content directive lets you pass other styles to mixins wherever they're included
-You call a mixin using the @include directive followed by the name of the mixin.
-The @extend directive shares sets of properties by goruping the selectors sharing    the same properties










// Partial imports
@import 'partials/variables';


// VARIABLES ------------------------------------ /

$white: #fff;

$color-primary: #278da4;
$color-secondary: #b13c69;
$color-accent: #eeea72;
$color-shade: #eee;

$color-text: #343434;
$color-bg: #3acec2;
$color-bg-light: #009fe1;

$font-stack-primary: 'Raleway', sans-serif;
$font-stack-secondary: 'Bree Serif', serif;

$max-width: 1000px;

// MIXINS ------------------------------------ /

@mixin skewed {
  position: relative;
  &::after {
    content: '';
    display: block;
    width: 100%;
    height: 50px; 
    position: absolute;
    transform: skewY(-2deg); 
    @content;
  }
}

@mixin center {
  width: 90%;
  max-width: $max-width;
  margin-left: auto;
  margin-right: auto;
}

/* BASE ------------------------------------------- */

* {
  box-sizing: border-box;
}

body {
  color: $color-text;
  font-size: 1rem;
  line-height: 1.5;
  font-family: $font-stack-primary;
  text-align: center;
  margin: 0;
}

h1,
h2 {
  font-family: $font-stack-secondary;
}

ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

p {
  margin-bottom: 1.25em;
  .intro & {
    font-size: 1.2em;
  }
}

a {
  color: $color-primary;
  text-decoration: none;
  &:hover {
    color: $color-secondary;  
  }
}

/* HEADER & FOOTER -------------------------------- */

header {
  height: 460px;
  background: linear-gradient($color-bg-light, $color-bg), url('../img/bg.jpg') no-repeat;
  background-blend-mode: multiply;
  background-size: cover;
  h1 {
    color: $white;
    font-size: 4.8em;
    margin-bottom: 0;
    letter-spacing: 1px;
  }
  p {
    color: $color-accent;
    font-size: 1.25em;
    margin: 0;
  }
  @inclue skewed {
    background-color: $white;
    bottom: -25px;
  }
}

footer {
  padding: 2em 0 0;
  height: 100px;
  background-color: $color-shade;
  margin-top: 3.5em;
  @include skewed {
    background-color: $color-shade;
    top: -25px;
  }
 } 
/* CONTAINERS ------------------------------------- */

.inner {
  padding: 0.5em 1em;
}

.intro {
  margin: auto;
  padding: 1em 1em 3em; 
}

/* COMPONENTS ------------------------------------- */

.main-nav {
  margin-top: 1em;
  li {
    display: inline-block;
    margin: 0 0.65em;
  }
  a {
    color: $white;
    font-size: 0.85em;
    text-decoration: none;
    text-transform: uppercase;
    padding: 0.5em;
    transition: 0.3s;
    &:hover {
      color: $color-accent;  
    }
  }
}

.img-featured {
  width: 165px;
  border: 4px solid $white; 
  border-radius: 50%;
  margin-top: 75px;
  position: relative;
  z-index: 100;
}

.card {
  display: flex;
  flex-direction: column;
  padding: 1.5em 1em;
  border: 1px solid $color-shade;
  border-radius: 0.25em;
  h1 {
    margin: 0.35em 0 0;
    line-height: 1.25;
  }  
  .icon,
  h1 {
    color: $color-primary;
  }
}

%clearfix {
  &::after {
      content: '';
      display: table;
      clear: both;
 }
}
%btn {
  color: $white;
  display: inline-block;
  font-weight: bold;
  text-decoration: none;
  text-transform: uppercase;
  padding: 0.75em 1.5em;
  border-radius: 0.35em;
  &:hover {
      color: $white;
      opacity: 0.8;
  }
  &:active {
      opacity: initial;
  }
 }
.btn {
    &-callout {
    @extend %btn;
    font-size: 1.1em;
    background-color: $color-secondary;
  }
  
  &-info {
    @extend %btn;
    font-size: 0.85em;
    background-color: $color-primary;  
    margin-top: auto;
  }
}  




/* MEDIA QUERIES ---------------------------------- */

@media (max-width: 575px) {
  header {
    height: 340px;
    h1 {
      font-size: 3.4em;
    }
  }
  .img-featured {
    display: none;
  }
}

@media (min-width: 576px) {
  .main-content {
    display: flex;
    flex-wrap: wrap;
  }  
  .card {
    flex: 1;
  }
}

@media (min-width: 768px) {
  .main-content {
    @include center;
  }
}

@media (min-width: 992px) {
  header {
    background-position: 0 0, 0 45%;
  }
  .intro {
    width: 45%;
  }
}


======================================
//  Partial Imports
======================================

// Utilities
@import 'utilities/variables',
        'utilities/mixins',
        'utilities/functions',
        'utilities/helpers';
        
// Base Styles     
@import 'base/reset',
        'base/base';

// Layout Styles
@import 'layout/containers',
        'layout/header',
        'layout/card',
        'layout/footer';

// Component Styles
@import 'components/nav',
        'components/buttons',
        'components/icons',
        'components/images';




