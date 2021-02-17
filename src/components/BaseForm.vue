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
                                    required
                                    @change="onChangeCategory">
                                    <option v-for="category of categories" :key="category.id" :value="category.id">{{category.name}}</option>
                                </select>
                            </b-col>
                        </b-row>
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
import CalculatorForm from './CalculatorForm.vue'
export default {
    name: 'BaseForm',
    components: {
        CalculatorForm
    },
    data() {
        return {
            categories: [{id:1, name:"Longitud"}, {id:2, name:"Monedas"}, {id:3, name:"Masa"}, {id:4, name:"Tiempo"}, {id:5, name:"Almacenamiento"}],
            measureUnits:[
                {id:1, categoryId:1, name:"N1"},
                {id:2, categoryId:1, name:"N2"},
                {id:3, categoryId:1, name:"N3"},
                {id:4, categoryId:2, name:"N4"},
                {id:5, categoryId:2, name:"N5"},
                {id:6, categoryId:2, name:"N6"},
                {id:7, categoryId:3, name:"N7"},
                {id:8, categoryId:3, name:"N8"},
                {id:9, categoryId:3, name:"N9"},
                {id:10, categoryId:4, name:"N10"},
                {id:11, categoryId:4, name:"N11"},
                {id:12, categoryId:4, name:"N12"},
                {id:13, categoryId:5, name:"N13"},
                {id:14, categoryId:5, name:"N14"},
                {id:15, categoryId:5, name:"N15"}
            ],
            selectedMeasureUnits:[
                {id:1, categoryId:1, name:"N1"},
                {id:2, categoryId:1, name:"N2"},
                {id:3, categoryId:1, name:"N3"}
            ]
            
        }
    },
    methods:{
        onChangeCategory(e){
            let categoryId = e.target.value;
            let values = this.measureUnits.filter(u => u.categoryId == categoryId);
            this.selectedMeasureUnits = values;
        }
    }
}
</script>

<style scoped>
    
</style>