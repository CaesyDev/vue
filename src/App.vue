<template>
    <h1>Hello world</h1>
    <PageViewer v-if="payload.length > 0" :navs="navNames" :active-pages="activePages"></PageViewer>
    <NavBar v-if="payload.length > 0" :updateIndex="updateParentIndex" :payload="payload" :validate="validate"></NavBar>
    <MyForm></MyForm>
</template>

<script>
import PageViewer from './components/PageViewer';
import NavBar from './components/NavBar';
import MyForm from './components/MyForm';
import '../node_modules/bootstrap/dist/css/bootstrap.css';

export default {
    
    components: {
        PageViewer,
        NavBar,
        MyForm
    },

    methods: {

        updateParentIndex: function(index){
            const length = this.navNames.length;
            if(index >= length){
                return false;
            }else{
                this.activePages = index;
            }
        },

        getData: async function(){
            let response = await fetch('pages.json');
            this.payload = this.navNames = await response.json();
            console.log(response);
        }
    },


    created(){
         this.getData();
    },


    data() {
        return {
            activePages: 0,
            isLightOn: false,
            theme: 'danger',
            link: "google.com",
            name: "Howell",
            counts: [1, 2, 3, 4],
            navNames: [],
            payload : [],
            validate:{
                name : "kc",
                age : "yh"
            }
        }
    },
}
</script>