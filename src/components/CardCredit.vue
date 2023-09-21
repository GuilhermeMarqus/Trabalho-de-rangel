<template>
       <div class="countainer" v-if="showCard">
        <div class="cardShow">
            <div class="insertName" >
                <input type="text" v-model="nomeCartao" placeholder="Seu Nome" >
            </div>
            <div class="insertValue">
                <input v-model="numero" type="number" placeholder="Valor a Adicionar">
            </div>
        </div>
        <div class="button">
            <button @click="clicarBotao" :disabled="numero <= 99">Criar Conta</button>
        </div>
    </div> 
    <div class="countainer" v-else>
        <div class="cardShow">
            <div class="nomeNoCartao">
                {{ nomeCartao }}
        </div>
    </div>
        <div class="saldo">
                <p>Saldo</p>
                <h1 :class="{ 'postivo': numero >= 0, 'negativo': numero < 0}">{{ numero }}</h1>
        </div> 
            
    
    <div class="valorAdicionado">
        <input type="number" v-model="valorAdicionado" :min="0" />
    </div>
    <div class="btn">
        <button @click="Depositar">Depositar</button>
        <button @click="Sacar">Sacar</button>
    </div>

</div>
</template>

<script>
    export default{
        name: 'CardCredit',

        data() {
        return {
            numero: 0,
            showCard: true,
            nomeCartao: '',
            valorAdicionado: 0,
        }
    },
    methods: {
        clicarBotao(){
            this.showCard = !this.showCard;
        },
        Depositar(){
            if (this.valorAdicionado > 0) {
                this.numero += this.valorAdicionado;
                this.valorAdicionado = 0;
            } else {
                alert('digite um valor.')
            }
        },
        Sacar(){
            if(this.valorAdicionado > 0){
                const Adcionado = this.numero - this.valorAdicionado;
                if(Adcionado >= -600 ){
                    this.numero = Adcionado;
                    this.valorAdicionado = 0;
                } else {
                    alert('Saldo insuficiente')
                }
            } else {
                alert('digite um valor')
            }
        }
    }
    }
    
</script>

<style>
.countainer{
    width: 400px;
    height: 200px;
    background: rgb(27, 170, 92);
    margin: 0 auto;
    border-radius: 20%;
}

.cardShow{
    padding-top: 45px;
    padding-right: 205px;
   
}

.insertName{

}

.insertValue{
    padding-top: 45px ;
}

.nomeNoCartao {
text-transform: uppercase;
text-align: center;
font-size: 17px;
font-weight: bold;
}

.saldo{

}

.button button{
    margin-top: 85px;
    padding-top: 10px;
    padding-bottom: 7px;
    background-color: #2c3e50;
    color: white;
    width: 140px;
    height: 40px;
    border-radius: 35%;
    border: none;
    font-size: 16px;
    cursor: pointer;
    
}

.btn{
    margin-top: 75px;
    margin-left: 135px;
}

.btn button{
    display: flex;
    margin-top: 10px;
    background-color: #2c3e50;
    color: white;
    width: 140px;
    height: 40px;
    border-radius: 35%;
    border: none;
    font-size: 16px;
    cursor: pointer;
    justify-content: center;
    align-items: center;
}

.button button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}

</style>