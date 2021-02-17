<template>
    <b-row class="justify-content-center mb-4">
        <b-col sm="5">
            <b-form-input
                class="p-4 text-center text-dark input-text-size"
                v-model="valueFrom"
                :value="valueFrom"
                type="text"
            ></b-form-input>
            <select name="valueFrom" id="valueFrom" 
                class="form-control form-select" 
                @change="onChangeMeasureFrom">
                <option v-for="measureUnit of measureUnits" :key="measureUnit.id" 
                    :value="measureUnit.id">{{measureUnit.name}}</option>
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
            ></b-form-input>
            <select name="valueResult" id="valueResult" 
                class="form-control form-select"
                @change="onChangeMeasureResult">
                <option v-for="measureUnit of measureUnits" :key="measureUnit.id" 
                    :value="measureUnit.id">{{measureUnit.name}}</option>
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
            valueResult: 1,
            selectedMeasureUnitFrom: 0,
            selectedMeasureUnitResult: 0
        }
    },
    methods:{
        onChangeMeasureFrom(e){
            // Obtenemos el valor de la unidad de medida (opcion) seleccionada
            let measureUnitId = e.target.value;
            console.log(measureUnitId);

            /*
                Logica de calculos acá si cambia la unidad de origen.
                Se puede verificar si ese id es el de una unidad de medida especifica, al ser valores estaticos
                ya se sabe cual sera, entonces si el id es igual a X numero se hace un calculo, sino otro.

                O incluso seria mucho mas eficiente tener un switch case.

            */

            // Asignamos el resultado
            this.valueResult = 12;
        },
        onChangeMeasureResult(e){
            // Obtenemos el valor de la unidad de medida (opcion) seleccionada
            let measureUnitId = e.target.value;
            console.log(measureUnitId);

            /*
                Logica de calculos acá si cambia la unidad de destino.
                Se puede verificar si ese id es el de una unidad de medida especifica, al ser valores estaticos
                ya se sabe cual sera, entonces si el id es igual a X numero se hace un calculo, sino otro.

                O incluso seria mucho mas eficiente tener un switch case.

            */

            // Asignamos el resultado
            this.valueResult = 13;
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