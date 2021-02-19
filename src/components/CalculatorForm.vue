<template>
    <b-row class="justify-content-center mb-4">
        <b-col sm="5">
            <b-form-input
                class="text-center text-dark input-size"
                v-bind:value="valueFrom"
                @keyup="onKeyupValueFrom"
                type="text"
            ></b-form-input>
            <select name="valueFrom" id="valueFrom" 
                class="form-control form-select" 
                @change="onChangeMeasureFrom">
                <option :value="selectedMeasureUnit" selected>Selecciona</option>
                <option v-for="measureUnit of measureUnits" :key="measureUnit.id" 
                    :value="measureUnit.id">{{measureUnit.name}}</option>
            </select>
        </b-col>
        <b-col sm="1" class="align-self-center mb-3 mb-sm-0">
            <span class="h2 d-none d-sm-block">=</span>
        </b-col>
        <b-col sm="5">
            <b-form-input
                class="text-center text-dark input-size"
                v-model="valueResult"
                type="text"
                readonly
            ></b-form-input>
            <select name="valueResult" id="valueResult" 
                class="form-control form-select"
                @change="onChangeMeasureResult">
                <option :value="selectedMeasureUnit" selected>Selecciona</option>
                <option v-for="measureUnit of measureUnits" :key="measureUnit.id" 
                    :value="measureUnit.id">{{measureUnit.name}}</option>
            </select>
        </b-col>
    </b-row>
</template>

<script>
import convert from 'convert-units'
import fx from 'money'
export default {
    name:'CalculatorForm',
    props:{
        measureUnits: Array
    },
    data() {
        return {
            valueFrom:1,
            valueResult: 1,
            selectedMeasureUnit: 0,
            selectedMeasureUnitFrom: 0,
            selectedMeasureUnitResult: 0
        }
    },
    methods:{
        onChangeMeasureFrom(e){
            this.selectedMeasureUnitFrom = parseInt(e.target.value);
            this.valueResult = getResult(this.valueFrom, this.selectedMeasureUnitFrom, this.selectedMeasureUnitResult);
        },
        onChangeMeasureResult(e){
            this.selectedMeasureUnitResult = parseInt(e.target.value);
            this.valueResult = getResult(this.valueFrom, this.selectedMeasureUnitFrom, this.selectedMeasureUnitResult);
        },
        onKeyupValueFrom(e){
            this.valueFrom = isNaN(parseInt(e.target.value)) ? "" : parseInt(e.target.value);
            this.valueResult = getResult(this.valueFrom, this.selectedMeasureUnitFrom, this.selectedMeasureUnitResult);
        }
    }
}

function getResult(valueFrom, selectedMeasureUnitFrom, selectedMeasureUnitResult){
    // Obtenemos el valor de la unidad de medida.
    let value = isNaN(parseInt(valueFrom)) ? "" : parseInt(valueFrom);
    if(selectedMeasureUnitFrom != 0 && selectedMeasureUnitResult != 0 && value != ""){
        
        /*
            Logica de calculos acá si cambia la unidad de destino.
            Se puede verificar si ese id es el de una unidad de medida especifica, al ser valores estaticos
            ya se sabe cual sera, entonces si el id es igual a X numero se hace un calculo, sino otro.

            O incluso seria mucho mas eficiente tener un switch case.

        */

        // Asignamos el resultado
        let valueResult = 10 + value;
        return valueResult;
    }
}
</script>

<style scoped>
    .form-select{
        margin-top: -2px;
    }

    .input-size{
        font-size: 180%;
        height: 46px;
        padding: 1px 6px;
    }
</style>