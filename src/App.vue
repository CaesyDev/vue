<template>
    <h1>Hello world</h1>
    <PageViewer :pages="navNames" :active-pages="activePages"></PageViewer>
    <NavBar :updateIndex="function(index){ activePages = index;}"></NavBar>
</template>

<script>
import PageViewer from './components/PageViewer';
import NavBar from './components/NavBar';

export default {
    components: {
        PageViewer,
        NavBar
    },
    data() {
        return {
            activePages: 0,
            isLightOn: false,
            theme: 'danger',
            link: "google.com",
            name: "Howell",
            counts: [1, 2, 3, 4],
            navNames: [
                {
                    name: "Home", link: "home.html", content: "This is the home page"
                }
                ,
                {
                    name: "About", link: "about.html", content: "This is the about page"
                },
                {
                    name: "License", link: "license.html", content: "This is the license page"
                },
                {
                    name: "Register", link: "register.html", content: "This is the registration page"
                }
            ]
        }
    },
}
</script>