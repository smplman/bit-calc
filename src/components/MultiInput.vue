<template>
    <div>
        <v-btn small @click="setType(10)" :color="buttons.dec">Dec(d)</v-btn>
        <v-btn small @click="setType(16)" :color="buttons.hex">Hex(x)</v-btn>
        <v-btn small @click="setType(2)" :color="buttons.bin">Bin(t)</v-btn>

        <span class="mx-5">Convert To</span>

        <v-btn small @click="convertTo(10)">Dec(d)</v-btn>
        <v-btn small @click="convertTo(16)">Hex(0x)</v-btn>
        <v-btn small @click="convertTo(2)">Bin(b)</v-btn>

        <v-text-field
            class="mt-5"
            :label="label"
            :placeholder="placeholder"
            :disabled=disabled
            v-bind:value="val"
            outlined
            @keyup="detectType"
        ></v-text-field>
    </div>
</template>

<script>
export default {
    props : {
        label: String,
        placeholder: String,
        disabled: Boolean,
        val: String
    },
    data() {
        return {
            type: 10,
            typeSet: false,
            buttons: {
                dec: '',
                hex: '',
                bin: ''
            }
        }
    },
    methods: {

        convertTo(base){
            console.log('convertTo', base);
            this.$emit('update:val', parseInt(this.val, this.type).toString(base));
            this.type = base;
            return 
        },

        isType(num, base){
            console.log('isType', num, base);
            let a = parseInt(num, base);
            return (a.toString(base) === num.toLowerCase());
        },

        detectType(e){
            console.log('detectType', num);
            let num = e.target.value;
            this.$emit('update:val', num);

            let isDec = this.isType(num, 10);
            let isHex = this.isType(num, 16);
            let isBin = this.isType(num, 2);

            console.log('isDec', isDec, 'isHex', isHex, 'isBin',isBin);

            if (!this.typeSet){
                this.buttons.dec = isDec ? 'success' : '';
                this.buttons.hex = isHex ? 'success' : '';
                this.buttons.bin = isBin ? 'success' : '';
                this.type = isBin ? 2 : (isHex ? 16 : 10);
            }

            return this.type;
            
        },

        setType(type){
            this.type = type;
            this.typeSet = true;

            this.buttons.dec = '';
            this.buttons.hex = '';
            this.buttons.bin = '';

            switch (type) {
                case 10:
                    this.buttons.dec ='primary';
                    break;
                case 16:
                    this.buttons.hex ='primary';
                    break;
                case 2:
                    this.buttons.bin ='primary';
                    break;
                
            }
        }
    }
}
</script>