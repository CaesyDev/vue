<template>
    <nav :class="navConditions">
        <div  id="navbarSupportedContent">
            <ul>
                <li v-for="(navName, index ) in payload" class="nav-item" :class="{active: activePage == index}"
                    :key="index">
                    <a  v-bind:title="`This links to the ${navName.name} page`" class="p"
                        v-on:click.prevent="update(index);" v-bind:href="navName.link">
                        {{ navName.name }}
                        <span class="sr-only">(current)</span></a>
                </li>
            </ul>
        </div>
        <button @click="updateTheme()">Change nav color</button>
    </nav>
</template>


<script>

export default {
    props:{
        updateIndex:{

        }, 

        payload:{

        }, 

        validate: {
            required: true, 
            type: Object,
            validator: value => {
                return (value && typeof value == "object" 
                              && typeof value.name === "string"
                              && typeof value.age === "number")
            }
        }
    },
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
        },


        linkEmphasis() {
            return {
                'emp': this.activePage
            }
        }


    },

    methods:{
        update(index){
            this.activePage = index;
            this.updateIndex(index);
        },

        updateTheme(){
            this.isLightOn = !this.isLightOn;
            localStorage.setItem("isLightOn", this.isLightOn);
        },

        getTheme(){
            return localStorage.getItem("isLightOn");
        }
    },


    data() {

        let x = this.getTheme();
        console.log(x);

        return {
            activePage:0,
            isLightOn: x,
            theme: 'danger',
            link : "google.com",
            name : "Howell",
            counts : [1, 2, 3, 4],
        }
    },
}
</script>

<style>
    .emp{
        text-decoration: underline;
    }
</style>