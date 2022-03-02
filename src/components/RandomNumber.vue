<template>
    <div class="logo">
        <img src="../assets/pcso-logo.png" alt="pcso-logo">
        <h1>My Lotto Generator</h1>
    </div>
    <button @click="generateNumber()" v-bind:class="isPlaying ? 'btnStyle' : '' " :disabled="isPlaying">{{btnText}}</button>
    <div class="container" v-if="showResults">
        <h3 class="randNumber" v-for="rand in randomNumber" :key="rand">
            {{ rand }}
        </h3>
    </div>
</template>


<script>
export default {
    props(){

    },
    data(){
        return {
            randomNumber: [],
            showResults: false,
            isPlaying: false,
            btnText: 'Generate lotto numbers',
        }
    },
    methods:{
        generateNumber(){
            

            let timeReset = 2500;


            while(this.randomNumber.length < 6){
                var r = Math.floor(Math.random() * 41) + 1;
                if(this.randomNumber.indexOf(r) === -1)
                    this.randomNumber.push(r);
            }
            this.showResults = true;
            this.isPlaying = true;
            if(this.isPlaying){
                this.btnText = "Please wait";
            }
            setTimeout(()=>{
                this.randomNumber = [];
                this.isPlaying = false;
                this.btnText = "Generate lotto numbers";
            },timeReset);
        },
        
    }
}
</script>

<style scope>

.container{
    position: absolute;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 10px;
    margin-left: 520px;
}
.randNumber{
    padding: 10px;
    margin: 10px;
}
img{
    width: 100px;
    height: auto;
}
.logo{
    display: flex;
    align-items: center;
    justify-content: center;
}
button{
   padding: 10px;
   margin-left: 10px;
}
.btnStyle{
    margin-left: 40px;
}
</style>