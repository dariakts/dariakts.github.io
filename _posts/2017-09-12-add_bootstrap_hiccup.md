---
layout: post
title: "Add Bootstrap to Clojure Hiccup"
---

## Hiccup

[Hiccup](https://github.com/weavejester/hiccup) is a library for representing HTML in Clojure. It uses vectors to represent elements, and maps to represent an element's attributes.

## Add twitter bootstrap to your webapp 

In your [Leiningen](https://github.com/technomancy/leiningen) created projet, create the following folders:

`resources/public/css`

`resources/public/js`

Download [Bootstrap](http://getbootstrap.com/docs/4.0/getting-started/download/), [jQuery](https://jquery.com/download/) and [Tether](https://github.com/HubSpot/tether/tree/master/dist/js) and add them to your _css_ and _js_ folders:

`css/bootstrap.min.js`

`js/bootstrap.min.js`

`js/jquery-3.2.1.min.js`

`js/tether.min.js`

Include those files in your hiccup generated pages. For example, if your have a function generating headers for your pages as follows:

~~~
(defn home-page
  []
  (page/html5
    (gen-page-head "Home") ; here it is 
    header-links
    [:h1 "Home"]
    [:p "Webapp to store and display some food."]))
~~~

You can include your css and js files in this function:

~~~
(defn gen-page-head
  [title]
  [:head
    [:title (str "Food expire: " title)]
    (page/include-css "/css/styles.css")
    (page/include-css "/css/bootstrap.min.css")
    (page/include-js "/js/tether.min.js")
    (page/include-js "/js/jquery-3.2.1.min.js")
    (page/include-js "/js/bootstrap.min.js")])
~~~

**Note:** `page` is `[hiccup.page :as page]`.
