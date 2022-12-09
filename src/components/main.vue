<template>
    <div class="main" >
        <MainGeneral v-if="actSide.activeMain"
                        :isActiveTitle="isActiveTitle"
                        @DB_History='DB_History'/>
        <MainHistory v-if="actSide.activeHistory"
                            :newBet="history"
                            :winOrLose="rez"
                            />
        <MainStatisticVue v-if="actSide.activeStat"/>

        
        
        
    </div>
</template>

<script>
import MainGeneral from "./mainComp/mainGen.vue";
import MainHistory from "./mainComp/mainHistory.vue";
import MainStatisticVue from "./mainComp/mainStatistic.vue";


export default{
    
    name: "MainComp",
    components:{
        MainStatisticVue,
        MainGeneral,
        MainHistory,
    },
    props:["isActiveTitle","actSide"],
    data(){
        return{
            history:"",
            rez:""
        } 
    },
    methods:{
        DB_History(el,winOrLose)
        {
            console.log(el,winOrLose);
            this.history = el
            this.rez = winOrLose
            
        }
       
    },
    

}

</script>

<style>
.main
{
    width: 100%;
    padding: 100px;
    background-color: var(--backgroundBlock);
}
.bett
    {
        position: relative;
        
        display: flex;
        border: 2px solid black;
        width: 300px;
        border-radius: 7px;
        background-color: #f9fdce;
        margin: 40px 0;
        
    }
    .info{padding: 10px;position: relative; margin: 0 auto;width: 200px; box-sizing: border-box;}
    .teams
    {
        font-weight: bold;
        font-size: 1.2em;
        text-align: center;
        border-bottom: .5px solid #000;
        padding-bottom: 5px;
        
    }
    .kff
    {
        position: absolute;
        top: 5px;
        right: -20px;
        color: #7f7f7f;
        font-weight: bold;
        background-color: #b0b0b055;
        padding: 5px 7px;
        border-radius: 4px;
        width: 20px;
        text-align: center;
    }
    .vinSum
    {
        padding: 20px 10px;
        text-orientation: mixed;
        writing-mode: vertical-rl;
        border-left: dashed 1px #000;
    }




.no-active,.ignore{display: none;}
main .active{display: flex;}
</style>