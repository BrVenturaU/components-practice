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
            // Deben ser 5 por cada categoria, los ID de las unidades de medida no se deben repetir.
            measureUnits:[
                // Longitud - Length
                {id:1, categoryId:1, name:"Milimeter", symbol:"mm"}, //Milimetros
                {id:2, categoryId:1, name:"Centimeter", symbol:"cm"}, //Centimetros
                {id:3, categoryId:1, name:"Inch", symbol:"in"}, //Pulgadas
                {id:4, categoryId:1, name: "Meter", symbol:"m"}, //Metros
                {id:5, categoryId:1, name:"Foot", symbol:"ft-us"}, //USA Feet

                // Monedas
                {id:6, categoryId:2, name:"Dolar estadounidense", symbol:"USD"}, // dolar estadounidense
                {id:7, categoryId:2, name:"Euro", symbol:"EUR"}, // euro - España
                {id:8, categoryId:2, name:"Colon Salvadoreño", symbol:"SVC"}, // euro - España
                {id:9, categoryId:2, name:"Libra esterlina", symbol:"GBP"}, // libra esterlina
                {id:10, categoryId:2, name:"Dolar de Hong Kong", symbol:"HKD"}, // dolar - Hong Kong

                   // Masa
                {id:11, categoryId:3, name:"Onza", symbol:"oz"},
                {id:12, categoryId:3, name:"Gramo", symbol:"g"},
                {id:13, categoryId:3, name:"Miligramo", symbol:"mg"},
                {id:14, categoryId:3, name:"Libra", symbol:"lb"},
                {id:15, categoryId:3, name:"Kilogramo", symbol:"kg"},

                //Tiempo

                {id:16, categoryId:4, name:"Milisegundo", symbol:"ms"},
                {id:17, categoryId:4, name:"Segundo", symbol:"s"},
                {id:18, categoryId:4, name:"Minutos", symbol:"min"},
                {id:19, categoryId:4, name:"Hora", symbol:"h"},
                {id:20, categoryId:4, name:"Día", symbol:"d"},

                //Almacenamiento -  Digital Storage
                {id:21, categoryId:5, name:"Bit", symbol: "b"},
                {id:22, categoryId:5, name:"Kilobyte", symbol: "Kb"},
                {id:23, categoryId:5, name:"Megabyte", symbol: "Mb"},
                {id:24, categoryId:5, name:"Gigabyte", symbol: "Gb"},
                {id:25, categoryId:5, name:"Terabyte", symbol: "Tb"}
            ],
             // Unidades de medida seleccionadas (Tienen que ser las 5 primeras, es decir, las de longitud)
                selectedMeasureUnits:[
                    {id:1, categoryId:1, name:"Milimeter", symbol:"mm"}, //Milimetros
                    {id:2, categoryId:1, name:"Centimeter", symbol:"cm"}, //Centimetros
                    {id:3, categoryId:1, name:"Inch", symbol:"in"}, //Pulgadas
                    {id:4, categoryId:1, name: "Meter", symbol:"m"}, //Metros
                    {id:5, categoryId:1, name:"Foot", symbol:"ft-us"}, //USA Feet
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