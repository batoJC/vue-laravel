<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Agregar registro</div>

                    <div class="card-body">
                        <form @submit.prevent="agregar">
                            <label for="identificacion">Identificación</label>
                            <input id="identificacion" class="form-control" type="text" v-model="persona.identificacion">
                            <label for="nombre">Nombres</label>
                            <input id="nombre" class="form-control" type="text" v-model="persona.nombre">
                            <label for="apellido">Apellidos</label>
                            <input id="apellido" class="form-control" type="text" v-model="persona.apellido">
                            <br>
                            <button class="btn btn-light hover-blue"><i class="fas fa-plus text-primary mr-2"></i>Agregar</button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
       data() {
            return {
            personas: [],
            modoEditar: false,
            persona: {
                nombre: '', 
                apellido: '',
                identificacion:''}
            }
        },
        created(){
            // axios.get('/notas').then(res=>{
            // this.notas = res.data;
            // })
        },
        methods:{
            agregar(){
                axios.post('personas',this.persona).then(res=>{
                    console.log(res);
                    if(res.data.res){
                        swal('Logrado!',res.data.msg,'success');
                    }else{
                        swal('Error!',res.data.msg,'error');
                    }
                });
            },
            eliminar(){
            }
        }
    }
</script>
