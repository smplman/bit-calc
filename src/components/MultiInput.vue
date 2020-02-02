<template>
    <div>
        <v-btn small @click="toDec">Dec(d)</v-btn>
        <v-btn small @click="toHex">Hex(0x)</v-btn>
        <v-btn small @click="toBin">Bin(b)</v-btn>
        <v-text-field
            class="mt-5"
            :label="label"
            :placeholder="placeholder"
            :disabled=disabled
            outlined
            v-model="calc"
            @keyup="detectType"
        ></v-text-field>
    </div>
</template>

<script>
export default {
    props : {
        label: String,
        placeholder: String,
        calc: String,
        disabled: Boolean
    },
    data() {
        return {

        }
    },
    methods: {

        toDec(num){
            console.log('toDec', num);
        },
        isDec(num){
            console.log('isDec', num);
            return false;
        },

        toHex(num){
            console.log('toHex', num);
        },
        isHex(num){
            console.log('isHex', num);
            let a = parseInt(num,16);
            return (a.toString(16) === num.toLowerCase())
        },

        toBin(num){
            console.log('toBin', num);
        },
        isBin(num){
            console.log('isBin', num);
            let re = new RegExp('^[0-1]{1,}$');
            return re.test(num);
        },

        detectType(e){
            console.log('detectType', num);
            let num = e.target.value;

            let isDec = this.isDec(num);
            let isHex = this.isHex(num);
            let isBin = this.isBin(num);

            console.log('isDec', isDec, 'isHex', isHex, 'isBin',isBin);
        }
    }
}
</script>