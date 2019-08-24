
# [Ramón Morcillo](https://www.ramonmorcillo.com/) notes from


# Learn Vue.js for free


## by Zaydek. [Course Link](https://scrimba.com/g/glearnvue) 



## Introduction to Vue.js

By just **adding a script** on an html file you can build both static and dynamic web pages. It has great documentation and community.


## Hello, Vue!

After adding the script on top of the file we can use in the **html**

```

<div id="app">

	<p>{{ message }}</p>

</div>

```

And then inside the **script** tag

```

var app = new Vue({

	el: "#app",

    data: {

        message: "hello, world!"

    }

})

```


## Methods

A property is part of a variable and **a method is a function that is attached to an object** or structure.

We define a method inside a methods object. 

```

// cast returns a spell (function) that decorates the wizard

function cast(emoji) {

    if (!emoji) {

        emoji = "¯\\_(ツ)_/¯"

    }

	return function (wizard) {

		return emoji + wizard + emoji

	}

}

var app = new Vue({

	el: "#app",

	data: {

		wizard: emojify("wizard")

	},

    methods: {

        lumos: cast(emojify("lumos")),

        incendio: cast(emojify("incendio"))

    }

})

```

And do not forget the html

```

<div id="app">

	<p v-html="incendio(lumos(wizard))"></p>

</div>

```


## Control Flow

Control flow is just a word that you can use to describe things like conditional logic, for loops, …  the way we control the flow of our program. We can use things like v-if and v-for for it.

```

<div id="app">

    	<p


    	v-for="wizard in wizards()"


    	v-html="wizard.name + ' ' + wizard.pet"

></p>

			

</div>

```


## Components

A component is to take some block of code into smaller blocks of code, making it simpler to maintain, update and read. If we would want to create a harry component in vue `<harry></harry>`, in the script tag we create a component and the vue syntax for it is:

```

Vue.component("harry", {

    template: `<p>` + emojify("harry") + `</p>`

})

```

We can also use properties on components which are called **props.** In the html we write this (do not forget the 2 dots :)

```

<div id="app">

            <wizard :name="harry"   ></wizard>

            <wizard :name="ron"     ></wizard>

            <wizard :name="hermione"></wizard>

</div>

```

Then in the script tag we refer the property `name`

```

Vue.component("wizard", {

    props: ["name"],

    template: `<p v-html="name"></p>`

})

```
