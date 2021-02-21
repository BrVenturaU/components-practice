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
                        
                        <b-row>
                            <b-col cols="12" class="text-left">
                                Lorem ipsum, dolor sit amet consectetur adipisicing elit. 
                            </b-col>
                        </b-row>
                        
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
                // Longitud
                {id:1, categoryId:1, name:"Metros", symbol:"m"},
                {id:2, categoryId:1, name:"N2"},
                {id:3, categoryId:1, name:"N3"},
                {id:4, categoryId:1, name:"N4"},
                {id:5, categoryId:1, name:"N5"},

                // Monedas
                {id:6, categoryId:2, name:"N6"},
                {id:7, categoryId:2, name:"N7"},
                {id:8, categoryId:2, name:"N8"},
                {id:9, categoryId:2, name:"N9"},
                {id:10, categoryId:2, name:"N10"},

                // Masa
                {id:11, categoryId:3, name:"N11"},
                {id:12, categoryId:3, name:"N12"},
                {id:13, categoryId:3, name:"N13"},
                {id:14, categoryId:3, name:"N14"},
                {id:15, categoryId:3, name:"N15"},

                //Tiempo
                {id:16, categoryId:4, name:"Milisegundo", symbol:"ms"},
                {id:17, categoryId:4, name:"Segundo", symbol:"s"},
                {id:18, categoryId:4, name:"Minutos", symbol:"min"},
                {id:19, categoryId:4, name:"Hora", symbol:"h"},
                {id:20, categoryId:4, name:"Día", symbol:"d"},
                //Almacenamiento
                {id:21, categoryId:5, name:"N21"},
                {id:22, categoryId:5, name:"N22"},
                {id:23, categoryId:5, name:"N23"},
                {id:24, categoryId:5, name:"N24"},
                {id:25, categoryId:5, name:"N25"}
            ],
            // Unidades de medida seleccionadas (Tienen que ser las 5 primeras, es decir, las de longitud)
            selectedMeasureUnits:[
                {id:1, categoryId:1, name:"Metros", symbol:"m"},
                {id:2, categoryId:1, name:"N2"},
                {id:3, categoryId:1, name:"N3"},
                {id:4, categoryId:1, name:"N4"},
                {id:5, categoryId:1, name:"N5"}
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