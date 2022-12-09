<template>
    <div class="side">
        <div class="id_profile side_f">
            <i class="bi bi-person-fill"></i><div class="name">{{name_profile}}</div>
            <div class="balans"><span>{{balanc}}</span>P</div>
        </div>
        <div class="main_content side_f">
            <div class="f"
                data-f="current"
                @click="isPanelMain">
                <p>Текущие</p>
            </div>
            <div class="f"
                data-f="history"
                @click="isPanelMain">
                <p>История</p>
            </div>
            <div class="f"
                data-f="static"
                @click="isPanelMain">
                <p>Статистика</p>
            </div>
        </div>
    </div>
    
</template>

<script>

export default{
    name: "SideNav",
    components:{
        
    },
    data(){
        return{
            balanc: 9000,
            name_profile: "Andrey99",
            act: {
                activeMain: true,
                activeHistory: false,
                activeStat:false
            },
        }
    },
    methods:{
        isPanelMain(e)
        { 
            let p
            
            for(p of document.querySelectorAll(".f p"))
            {
                p.classList.remove("active")
            }
            e.target.classList.add("active")
            switch(e.target.parentElement.dataset.f)
            {
                case "current":
                    this.act.activeMain = true
                    this.act.activeHistory = false
                    this.act.activeStat = false
                break
                case "history":
                    this.act.activeMain = false
                    this.act.activeHistory = true
                    this.act.activeStat = false
                    break
                case "static":
                    this.act.activeMain = false
                    this.act.activeHistory = false
                    this.act.activeStat = true
                break
            }
            
            this.$emit("act",this.act)
            
        }
    }
}
</script>

<style scoped>
.side
{
    text-align: right;
    font-size:large;
    box-sizing: border-box;
    width: 250px;
    height: 800px;
    padding: 100px 0;
    color: var(--textInBlockDop);
    background-color: var(--backgroundBlockDop);
}
.side .name
{
    margin-bottom: 10px;
    font-weight: bold;
}
.side .name::before
{
    content: "\F4E1";
    font-weight: 900;
    display: inline-block;
    margin-right: 10px;
    color: var(--textInBlockDop);
}
.id_profile
{
    margin-bottom: 50px;
    padding: 0 50px;
}
.f:hover
{
    transition: all .2s ease;
    background-color:#e1e1e12c;
    cursor: pointer;
}
.f p{padding: 10px 50px;}
.f p.active{color: var(--lineHover);}
</style>