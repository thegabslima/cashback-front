<script setup>
import axios from 'axios'
import { ref } from 'vue'


let listTransaction = ref([]);

    const fetchTransactions = async () => {
        await axios.get('http://localhost:3000/transactions/all').then(response => {
            if (response.data.type == "success") {
                listTransaction = response.data.data
            }
        })  
    }

    await fetchTransactions()

    const formatAmount = (amount) => {
        return new Intl.NumberFormat('pt-BR', { style: 'currency', currency: 'BRL' }).format(amount)
    }

    const formatDate = (date) => {
        return new Intl.DateTimeFormat('pt-BR').format(new Date(date))
    }

</script>

<template>
    <div>
        <div class="container">
        <ul class="list_transactions" >
            <li class="item_list_transactions" v-for="item in listTransaction" :key="item.id">
                <!-- format amount with BRL currency -->
                <div><b>Nome</b>: {{ item.full_name }}</div>
                <div><b>Descrição</b>: {{ item.description }}</div>
                <div><b>Valor</b>: {{ formatAmount(item.amount) }}</div>
                <div><b>Taxa</b>: {{ item.tax }}%</div>
                <div><b>Data</b>: {{ formatDate(item.date) }}</div>
                <div><b>Parcelas</b>: {{ item.installment }}</div>
                <hr>
                <div><b>Valor da Taxa</b>: {{ formatAmount(item.amountTax) }}</div>
                <br>
                <ul class="installments">
                    <li v-for="i in item.installments" :key="i.installment">
                        {{ console.log(item) }}
                        <div><b>Parcela:</b> {{ i.installment < 10 ? "0" + i.installment : i.installment  }} - <b>Valor:</b> R$ {{ (i.amount) }} - <b>Cash Back:</b> R$ {{ i.cashBack }}</div>
                    </li>
                </ul>
                <hr>
            </li>
        </ul>
        </div>
    </div>
</template>

<style>
    /*  */
    h4 {
        color: #333;
    }
    ul {
        list-style-type: circle;
        padding: 0;
        display: flex;
        justify-content: center;
    }
    .list_transactions{
        padding: 0;
        list-style-type: none;
        color: #fff;
    }
    .list_transactions li {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
    }
    .list_transactions li div {
        padding: 4px;
    }
    .item_list_transactions{
        margin: 25px;
        padding: 20px;
        background: #004292;
        width: 25%px;
        border-radius: 10px;
        box-shadow: 2px 1px 1px 1px rgba(183, 183, 183, 0.18);
        display: flex;
    }
    hr {
        width: 100%;
    }
    .installments{
        display: flex;
        flex-direction: column;
        margin: 5px;
    }
    .installments li{
        padding:10px;
    }
    .installments li:nth-child(odd){
        
        background: #0053b8;
    }
</style>