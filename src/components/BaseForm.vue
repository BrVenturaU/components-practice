<template>
    <b-row>
        <b-col cols="12" sm="8" class="mx-auto">
            <div class="card p-4 rounded-lg shadow">
                <div class="card-body">
                    <b-form>
                        <b-row class="mb-4">
                            <b-col>
                                <select name="category" id="category" 
                                    class="form-control" 
                                    @change="onChangeCategory">
                                    <option v-for="category of categories" :key="category.id" :value="category.id">{{category.name}}</option>
                                </select>
                            </b-col>
                        </b-row>
                        <!-- Componente con los inputs para cálculos al cual le enviamos las categorias seleccionadas -->
                        <CalculatorForm :measureUnits="selectedMeasureUnits" />
                        
                    </b-form>
                </div>
            </div>
        </b-col>
    </b-row>
</template>

<script>
// Importamos el componente hijo
import CalculatorForm from './CalculatorForm.vue'
export default {
    name: 'BaseForm',
    components: {
        CalculatorForm
    },
    data() {
        return {
            // Categorias de medición
            categories: [{id:1, name:"Longitud"}, {id:2, name:"Monedas"}, {id:3, name:"Masa"}, {id:4, name:"Tiempo"}, {id:5, name:"Almacenamiento"}],

            // Unidades de medida (cada categoryId corresponde a un id de las categorias anteriores)
            measureUnits:[
               /* {id:1, categoryId:1, name:"N1"},
                {id:2, categoryId:1, name:"N2"},
                {id:3, categoryId:1, name:"N3"},*/
                {id:6, categoryId:2, name:"USD"}, // dolar estadounidense
                {id:7, categoryId:2, name:"EURO"}, // euro - España
                {id:8, categoryId:2, name:"GBP"}, // libra esterlina
                {id:9, categoryId:2, name:"HKD"}, // dolar - Hong Kong
                {id:10, categoryId:2, name:"AED"}, // dirham - Emiratos Arabes
                {id:11, categoryId:3, name:"Onza", symbol:"oz"},
                {id:12, categoryId:3, name:"Gramo", symbol:"g"},
                {id:13, categoryId:3, name:"Miligramo", symbol:"mg"},
                {id:14, categoryId:3, name:"Libra", symbol:"lb"},
                {id:15, categoryId:3, name:"Kilogramo", symbol:"kg"},
                /*{id:10, categoryId:4, name:"N10"},
                {id:11, categoryId:4, name:"N11"},
                {id:12, categoryId:4, name:"N12"},
                {id:13, categoryId:5, name:"N13"},
                {id:14, categoryId:5, name:"N14"},
                {id:15, categoryId:5, name:"N15"}*/
            ],
            // Unidades de medida seleccionadas
            selectedMeasureUnits:[
                {id:1, categoryId:1, name:"N1"},
                {id:2, categoryId:1, name:"N2"},
                {id:3, categoryId:1, name:"N3"}
            ]
            
        }
    },
    methods:{
        onChangeCategory(e){
            // Obtenemos el valor de la categoria (opcion) seleccionada mediante el evento onchange
            let categoryId = e.target.value;
            // Filtramos aquellas unidades de medida donde su atributo categoryId sea igual al categoryId seleccionado
            let values = this.measureUnits.filter(u => u.categoryId == categoryId);
            // Configuramos nuestras unidades de medida seleccionadas con dichos valores.
            this.selectedMeasureUnits = values;
        }
    }
}
</script>

<style scoped>
    
</style>