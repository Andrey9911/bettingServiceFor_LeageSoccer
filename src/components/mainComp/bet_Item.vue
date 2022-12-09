<template>
    <div class="bett" @mouseenter="mouseEnter" @mouseleave="mouseLeave">
        <div class="vinOrProg" ref="rez">
            <input type="text" placeholder="1" maxlength="1">
            <input type="text" placeholder="2" maxlength="1" @input="score">
        </div>
        <div class="info">
            <div class="teams">{{item.teams.title1}}-{{item.teams.title2}}</div>
            <div class="info_bet">
                <div class="kff">{{item.kff}}</div>
                {{item.event}} | {{item.sum}}rub.
            </div>
        </div>
        <div class="vinSum">{{item.sum * item.kff}}</div>
    </div>
</template>

<script>


export default {
    // name: 'betItem',
    props:["item"],
    data(){
        return{
            scoreCustom:{
                point1:"",
                point2:""
            },
            rezult: false
        }
        
    },
    methods:{
        mouseEnter()
        {
            this.$refs.rez.classList.add("active")
        },
        mouseLeave(){this.$refs.rez.classList.remove("active")},
        score(el)
        {
            let ev = this.item.event
            if(this.$refs.rez.children[0].value == "")
            {
                this.$refs.rez.children[0].classList.add("invalid")
            }
            else if(this.$refs.rez.children[0].value != "" && el.target.value != "")
            {
                this.$refs.rez.classList.remove("active")

                this.scoreCustom.point1 = this.$refs.rez.children[0].value
                this.scoreCustom.point2 = el.target.value

                this.rezult = true
                // console.log(checkEvent(parseInt(this.scoreCustom.point1),parseInt(this.scoreCustom.point2)))
                this.$emit("delElWithArray",this.item,checkEvent(parseInt(this.scoreCustom.point1),parseInt(this.scoreCustom.point2)))

            }


            
            function checkEvent(one,second)
            {
                
                if(ev == "1x" && one > second) return true
                else if(ev == "2x" && one < second) return true
                else if(ev == "н" && one == second)return true
                else return false
            }
        }
    }

}
</script>

<style scoped>
 
    .vinOrProg
    {
        padding: 10px 30px;
        border-radius: 7px;
        background-color: #f9fdce;
        position: absolute;
        right: -185px;
        display: none;
        
    }
    .vinOrProg.active
    {
        display: block;
    }
    .vinOrProg input
    {
        font-weight: bold;
        width: 40px;
        height: 50px;
        margin: 0 10px;
        border: none;
        box-sizing: border-box;
        border-radius: 5px;
        padding: 5px 15px;
    }
    .vinOrProg input::placeholder{color: rgba(0, 0, 0, 0.159);}
</style>