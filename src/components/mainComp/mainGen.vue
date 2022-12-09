<template>
    <div class="main_general">
      <h2>Текущие</h2>
        <AddBet v-if="isActiveTitle" 
                @addBet="newstavka"
                :index="id_betLength"/>
        
        <bet_Item v-for="item of bets_list"  :key="item.id"
                    :item="item"
                    @delElWithArray="delElWithArray"/>
    </div>
</template>

<script>
import AddBet from '../addBet.vue';
import bet_Item from './bet_Item.vue';
import DataBase from '../../DataBaseCurrent' 
import betListHistory from '../../DataBaseHistory';

export default {
  name: 'mainGen',
  props:["isActiveTitle"],
  components:{
    AddBet,
    bet_Item
    },
  data(){
    return{
        bets_list: DataBase,
        DBHistory:betListHistory,
        id_betLength: DataBase.length
    }
    
  },
  methods:{
    delElWithArray(obj,WorL)
    {
        let bets = this.bets_list
        let curInd = bets.indexOf(obj)
        // console.log(obj,sc);
        console.log()
        if(curInd == bets.length - 1)
        {
            this.DBHistory.push(obj);
            console.log(this.DBHistory,WorL);
            this.$emit("DB_History",this.DBHistory,WorL);

            bets.pop()
        }
        else
        {
            this.DBHistory.push(obj);
            this.$emit("DB_History",this.DBHistory,WorL);
            
            [bets[curInd],bets[bets.length - 1]] = [bets[bets.length - 1],bets[curInd]]
            bets.pop()
        }
    },
    newstavka(bet)
    {
        
        this.bets_list.push(bet)
        console.log(DataBase);
    }
  }
}
</script>

<style>
    .main_general{width: 100%;}
    .main_general ul li{margin: 50px 0;}
    
</style>