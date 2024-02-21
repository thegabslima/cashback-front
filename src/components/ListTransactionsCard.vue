
<script>
    import ListTransaction from './ListTransactions.vue'

    export default {
        name: 'ListTransactionCard',
        components: {
            ListTransaction
        }
    }
</script>

<template>
    <Suspense>
    <template #default>
            <div class="card card_list_user">
                <ListTransaction />
            </div>
    </template>
    <template #fallback>
        <span>Loading...</span>
    </template>
 </Suspense>
</template>

<style>
    .card_list_user{
        padding: 20px;
    }
</style>