<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
        <input  type="text" placeholder="escribe aqui" @change="changeInline"  v-model="valueInput" />
        <button v-on:click="changeInputValue">cambiar</button>
        <button v-on:click="valueInput = 'cambio inline'">cambiar inline</button>
        <p>Valor del input: <strong>{{ valueInput }}</strong></p>
        <p>Tamanio: {{ valueInput.length }}</p>
        <!---
        <input type="text" placeholder="escribe aqui" v-model="firstName" />
        <input type="text" placeholder="escribe aqui" v-model="lastName" />
        <p>Fullname: <strong>{{ fullName }}</strong> </p>
        -->
        
        
        <!--
        
                <button @click="callParent">llamando al padre</button>

        -->
    </div>
</template>

<script>

export default {
    name: 'HelloWorld',
    props: {
        msg: String,
        type: {
            type: Number,
            default: 100
        }
    },
    data() {
        return {
            valueInput: '',
            firstName: '',
            lastName: '',
        }
    },
    watch: {
        valueInput: function (newVal, oldVal) {
            console.warn('valor viejo: ' + oldVal);
            console.error('nuevo valor: ' + newVal);
        }
    },
    computed: {
        fullName: function () {
            return this.firstName + ' ' + this.lastName
        }
    },
    methods: {
        changeInputValue() {
            this.valueInput = 'cambiando valor';
        },
        changeInline(){
            console.log('---- cambiando valor inline ----', this.valueInput);
        },
        callParent(){
            this.$emit('fromChild',{ msg: this.valueInput })
        },
        callFromParent(value){
            this.valueInput = value;
            console.log('---- llamando al hijo ----');
        }
    },
    created() {
        console.log('created');
    },
    mounted() {
        console.log('mounted');
        console.warn('en mounted', this.type);
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
    margin: 40px 0 0;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}
</style>
