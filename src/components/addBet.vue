<template>
    <div class="form"
        ref="card">
        <h2 style="margin-bottom: 50px;">create Bet</h2>
            <form action="" ref="form" name="card_form">
                <input class="title1 inpT" 
                        placeholder="команда 1..."
                        ref="inp1"><br/>
                <input class="title2 inpT" placeholder="команда 2..." ref="inp2">
                <div class="details">
                    
                    <input type="radio" name="ev" id="ev1">
                    <label for="ev1">1x</label>
                    
                    <input type="radio" name="ev" id="ev2">
                    <label for="ev2">2x</label>
                    
                    <input type="radio" name="ev" id="ev3">
                    <label for="ev3">н</label>
                    
                    <input type="radio" name="ev" id="ev4">
                    <label for="ev4"></label>
                </div>
                <div class="startSum">
                    <input type="number" class="inpT" name="" id="money" min="500" step="100" value="500">
                </div>
                <div class="sub" @click="add"><span>Создать</span></div>
            </form>
    </div>
</template>

<script>
class newObjectForBet{
        teams = {
            title1: "",
            title2:""
        }
        score = {
            point1: "",
            point2: "",
        }
        constructor(id,team1,team2,kf,ev,money)
            {
                this.id = id
                this.teams.title1 = team1
                this.teams.title2 = team2
                this.sum = money
                this.score.point1 = Math.round(Math.random() * (5 - 0) + 0)
                this.score.point2 = Math.round(Math.random() * (5 - 0) + 0)
                this.kff = kf
                this.event = ev

            }
    }

export default{
    
    name: "AddBet",
    props: ["index"],
    data(){
        return{
        } 
    },
    methods:{
        add()
        {
            let ev;
            console.log(this.$refs);
            for(let i = 0; i < this.$refs.form.length; i++)
            {
                
                let inp = this.$refs.form[i]
                if(inp.value == "")
                {
                    
                    inp.classList.add("invalid")
                    inp.classList.add("invalid-anim")
                    setTimeout(() => {inp.classList.remove("invalid-anim")},100)
                } 
                else inp.classList.remove("invalid")
                
            }
            for(let el of this.$el.querySelectorAll("input[type='radio']"))
            {
                if(el.checked)ev = el.labels[0].textContent
            }
            if(this.$refs.form[0].value == "" && this.$refs.form[1].value == "") return
            
            let newBet = new newObjectForBet(
                                    this.index + 1,
                                    this.$refs.form[0].value,
                                    this.$refs.form[1].value,
                                    this.randomKF(1,5),
                                    ev,
                                    this.$refs.form[6].value)
                    
            this.$emit("addBet",newBet);

            
        },
        randomKF(min,max){
            return (Math.random() * (max - min) + min).toFixed(1)
        }
    }

}
</script>
<style>

    .form
    {
        z-index: 5;
        position: absolute;
        top: 50px;
        right: 50px;
        background-color: #f9fdce;
        border: 1px solid #000;
        padding: 20px;
        width: 700px;

    }
    .inpT
    {
        border-radius: 30px;
        width: 200px;
        padding: 10px 15px;
        margin: 10px 0;
        border: none;
    }
    .inpT:hover
    {
        transition: all .4s ease;
        border: 1px solid var(--lineHover);
    }
    .details
    {
        width: 50%;
        margin: 0 auto;

    }
    .details input[type="radio"]
    {
        margin: 20px;

    }
    .details input[type="radio"]
    {
        opacity: 0;
    }
    .details  input[type="radio"]+label::before
    {
        content: "";
        display: inline-block;
        width: 20px;
        height: 20px;
        border-radius: 2px;
        background-color: #fff;
    }
    .details input[type="radio"]:checked+label::before
    {
        content: "";
        display: inline-block;
        background-color: var(--lineHover);
        border: none;
        /* background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 8 8'%3e%3cpath fill='%23fff' d='M6.564.75l-3.59 3.612-1.538-1.55L0 4.26 2.974 7.25 8 2.193z'/%3e%3c/svg%3e");    */
    }
    .sub
    {
        cursor: pointer;
        position: relative;
        background-color: var(--backgroundBlockDop);
        color: var(--textInBlockDop);
        padding: 5px 10px;
        width: fit-content;
        font-weight: bold;
        transition: all .3s ease;
    }
    .sub span{z-index: 5;}
    .sub::before
    {
        position: absolute;
        content: "";
        top: 0;
        left: 0;
        width: 0;
        height: 100%;
        background: var(--backgroundBlockHover);
        transition: all .35s;
    }
    .sub:hover::before{
        width: 100%;
    }
    .invalid
    {
        border: 1px solid red;
        
    }
    .invalid-anim{animation: invalid .3s ease;}
    input.invalid:before
    {
        content: "dv";
        display: block;
        color: red;
    }
    .money
    {

    }
    @keyframes invalid {
        0%
        {
            transform: translateX(-7px);
        }
        40%{transform: translateX(7px);}
        80%{transform: translateX(-5px);}
        100%{transform: translateX(5px);}
    }
</style>
