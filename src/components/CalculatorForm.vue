<template>
    <b-row class="justify-content-center mb-4">
        <b-col sm="5">
            <b-form-input
                class="p-4 text-center text-dark input-text-size"
                v-model="valueFrom"
                :value="valueFrom"
                type="text"
                required
            ></b-form-input>
            <select name="valueFrom" id="valueFrom" 
                class="form-control form-select" 
                required>
                <option v-for="measureUnit of measureUnits" :key="measureUnit.id" :value="measureUnit.id">{{measureUnit.name}}</option>
            </select>
        </b-col>
        <b-col sm="1" class="align-self-center mb-3 mb-sm-0">
            <span class="h2 d-none d-sm-block">=</span>
        </b-col>
        <b-col sm="5">
            <b-form-input
                class="p-4 text-center text-dark input-text-size"
                v-model="valueResult"
                type="text"
                required
            ></b-form-input>
            <select name="valueResult" id="valueResult" 
                class="form-control form-select" 
                required>
                <option v-for="measureUnit of measureUnits" :key="measureUnit.id" :value="measureUnit.id">{{measureUnit.name}}</option>
            </select>
        </b-col>
    </b-row>
</template>

<script>
export default {
    name:'CalculatorForm',
    props:{
        measureUnits: Array
    },
    data() {
        return {
            valueFrom:1,
            finalValueResult: 1
        }
    },
    computed:{
        valueResult(){
            let valueFrom = parseInt(this.valueFrom);
            return this.finalValueResult + valueFrom;
        }
    },
    methods:{
        onChangeValueFrom(e){
            this.finalValueResult = e.target.value;
        }
    }
}
</script>

<style scoped>
    .form-select{
        margin-top: -2px;
    }

    .input-text-size{
        font-size: 180%;
    }
</style>