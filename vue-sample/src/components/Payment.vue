<script setup lang="ts">
import { ref, reactive, computed, watch, toRefs } from 'vue'

const itemName1 =ref<string>('Desk')
const itemName2 ='Chair'


const item1 = reactive({
    name: 'Desk',
    price: 40000,
    url: 'google.com'
})

// const price1 = 40000
const price2 = 20000


// const url1 = 'google.com'
const url2 = 'yahoo.com'

// 購入ボタンをクリックしたときの関数
const buy = (itemName: string) => {
    alert('Are you sure to buy'+ itemName + '?')
}

const input = (event:any) => {
    item1.name = event.target.value
}

const inputPrice = (event:any) => {
    item1.price = event.target.value
}

const budget = 50000

// // 計算を行う場合にはcomputedを使うのが推奨されてる
// const priceLabel = computed(() => {
//     if (item1.price > budget) {
//         return 'too expensive ...'
//     } else {
//         return item1.price + 'yen'
//     }
// })

// 以下はwatchを使った場合（基本はcomputedでいい）
const priceLabel = ref<string>(item1.price + 'yen')
const { price } = toRefs(item1)
watch(price, () => {
        if (price.value > budget) {
        priceLabel.value = 'too expensive ...'
    } else {
        priceLabel.value =  price.value + 'yen'
    }
})

</script>

<template>
    <div class="container">
        <h1>最近の支出</h1>
        <input v-on:input="input"/>
        <input v-on:input="inputPrice"/>

        <div class="payment">
            <label>{{ item1.name }}</label>
            <label>{{ priceLabel }}</label>
            <a v-bind:href="item1.url">bought at ...</a>
            <button v-on:click="buy(itemName1)">BUY</button>
        </div>

        <div class="payment">
            <label>{{ itemName2 }}</label>
            <label>{{price2}}円</label>
            <a v-bind:href="url2">bought at ...</a>
        </div>
    </div>
</template>

<style scoped>
.countainer {
    display: flex;
    flex-direction: column;
    align-items: center;
}
.payment {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 80px;
    width: 400px;
    background-color: aliceblue;
    margin-bottom: 8px;
}
input {
    margin-bottom: 8px;
}
label {
    font-size: 20px;
    font-weight: bold;
}
</style>