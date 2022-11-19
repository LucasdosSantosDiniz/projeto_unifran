<template>
    <div>
        <div>
            <Message :msg="msg" v-show="msg"/>
            <form @submit="createBurger">
                <div class="input-container">
                    <label for="nome">Nome do Cliente:</label>
                    <input type="text" id="nome" name="name" v-model="nome" placeholder="Nome completo">
                </div>
                <div class="input-container">
                    <label for="pao">Escolha seu pão:</label>
                    <select name="pao" id="pao" v-model="pao">
                        <option value="">Tipos de Pães:</option>
                        <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">
                            {{pao.tipo}}
                        </option>
                    </select>
                </div>
                <div class="input-container">
                    <label for="carne">Escolha sua carne:</label>
                    <select name="carne" id="carne" v-model="carne">
                        <option value="">Tipos de Carnes:</option>
                        <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">
                            {{carne.tipo}}
                        </option>
                    </select>
                </div>
                <div id="opcionais-conatainer" class="input-container">
                    <label id="opcionais-title" for="opcionais">Opcionais:</label>
                    <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
                        <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                        <span> {{opcional.tipo}}</span>
                    </div>
                </div>
                <div class="input-container">
                    <input type="submit" class="btn-burguer" value="FAZER PEDIDO">
                </div>
            </form>
        </div>
    </div>
</template>

<script>
import Message from './Message.vue'
export default{
    name:"Form",
    components:{
        Message
    },
    data() {
        return {
            paes: null,
            carnes: null,
            opcionaisdata: null,
            nome: null,
            pao: null,
            carne: null,
            opcionais: [],
            msg: null
        };
    },

    methods:{
        async getIngredientes(){
            const req = await fetch("http://localhost:3000/ingredientes")
            const data = await req.json()

            this.paes = data.paes
            this.carnes = data.carnes
            this.opcionaisdata = data.opcionais
        },
        async createBurger(e){
            e.preventDefault()

            const data ={
                nome:this.nome,
                carne: this.carne,
                pao: this.pao,
                opcionais: Array.from(this.opcionais),
                staus: 'Solicitado'
            }

            const dataJson = JSON.stringify(data)

            const req = await fetch("http://localhost:3000/burgers",{
                method:"POST",
                headers:{"Content-Type": "application/json"},
                body:dataJson
            })

            const res = await req.json()

            // colocar uma mensagem de pedido
            this.msg =` Pedidio Nº ${res.id} realizado com sucesso !`

            // limpar mensagem
            setTimeout (() => this.msg = "", 5000)

            // limpar os campos
            this.nome = ""
            this.carne = ""
            this.pao = ""
            this.opcionais = ""

        },
    }, 

    mounted(){
        this.getIngredientes()
    }
}
</script>

<style scoped>
form{
    max-width: 400px;
    margin: 0 auto;
}
.input-container{
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}

label{
    font-weight: bold;
    margin-bottom: 15px;
    color: #222;
    padding: 5px 10px;
    border-left: 4px solid red;
}
input, select{
    padding: 5px 10px;
    width: 300px;
}
#opcionais-conatainer{
    flex-direction: row;
    flex-wrap: wrap;
}
#opcionais-title{
    width: 100%;
}
.checkbox-container{
    display: flex;
    align-items: flex-start;
    width: 50%;
    margin-bottom: 20px;
}

.checkbox-container span,.checkbox-container input{
    width: auto;
}
.checkbox-container span{
    margin-left: 6px;
    font-weight: bold;
}

.btn-burguer{
    background-color: rgb(255, 208, 0);
    color:  red;
    font-weight: bold;
    border: 20px solid transparent;
    border-radius: 30px;
    padding: 2px;
    font-size: 20px;
    margin: 0;
    cursor: pointer;
    transition: .5s;
}
.btn-burguer:hover{
    background-color: transparent;
    color:black;
}
</style>