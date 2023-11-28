<template>
    <nav :class="navConditions">
        <a class="navbar-brand" href="#">Navbar</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
                <li v-for="(navName, index ) in payload" class="nav-item" :class="{ active: activePage == index }"
                    :key="index">
                    <a v-bind:title="`This links to the ${navName.name} page`" class="nav-link"
                        v-on:click.prevent="activePage = index; updateIndex(index)" v-bind:href="navName.link">
                        {{ navName.name }}
                        <span class="sr-only">(current)</span></a>
                </li>
            </ul>
        </div>
        <button @click="isLightOn = !isLightOn">Change nav color</button>
    </nav>
</template>

<script>
export default {

    props:['updateIndex'],
    computed: {
        navConditions() {
            return {
                'light': this.isLightOn,
                'dark': !this.isLightOn
            }
        },


        navArray() {
            return [
                this.isLightOn ? 'light' : '',
                !this.isLightOn ? 'dark' : ''
            ];
        }


    },


    data() {
        return {
            activePage:0,
            isLightOn:false,
            theme: 'danger',
            link : "google.com",
            name : "Howell",
            counts : [1, 2, 3, 4],
            payload : [
                {
                    name : "Home", link : "home.html", content : "This is the home page"
                }
                , 
                {
                    name : "About", link : "about.html", content : "This is the about page"
                },
                {
                    name : "License", link : "license.html", content : "This is the license page"
                }, 
                {
                    name : "Register", link : "register.html", content : "This is the registration page"
                }
            ]
        }
    },
}
</script>