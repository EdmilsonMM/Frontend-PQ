<template>
        <div class="flex w-full justify-center">
        <div class=" flex bg-gray-800 w-full max-w-6xl p-8  rounded-xl shadow-lg text-white justify-center">
            
            <table class="bg-gray-800 text-white shadow-lg w-full ">
                <thead>
                    <tr>
                        <th class="border border-gray-400 px-4 py-2">Usuario</th>
                        <th class="border border-gray-400 px-4 py-2">RazonSocial</th>
                        <th class="border border-gray-400 px-4 py-2">Cargo</th>
                        <th class="border border-gray-400 px-4 py-2">Celular</th>
                        <th class="border border-gray-400 px-4 py-2">Correo</th>
                        <th class="border border-gray-400 px-4 py-2">Mensaje</th>
                        <th class="border border-gray-400 px-4 py-2">Accion</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="user of usuarios" :key="user" >
                        <td class="border border-gray-400 px-4 py-2">{{user.usuario}}</td>
                        <td class="border border-gray-400 px-4 py-2">{{user.razonSocial}}</td>
                        <td class="border border-gray-400 px-4 py-2">{{user.cargo}}</td>
                        <td class="border border-gray-400 px-4 py-2">{{user.celular}}</td>
                        <td class="border border-gray-400 px-4 py-2">{{user.correo}}</td>
                        <td class="border border-gray-400 px-4 py-2">{{user.mensaje}}</td>
                        <td class="flex flex-row justify-around pt-2 border border-gray-400">
                            <button @click="deleteUser(user._id)" class="text-red-500 py-3">Eliminar</button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                usuarios : []
            }
        },
        methods:{
             async listarUsuarios(){
                const response = await fetch('https://api-expre.herokuapp.com/api/formulario');
                const data = await response.json();
                this.usuarios = data
            },
            async deleteUser(id){
                const res = await fetch('https://api-expre.herokuapp.com/api/formulario/'+id,{
                    method : 'DELETE',
                    headers : {
                        'Accept': 'application/json',
                        'Content-type':'application/json'
                    }
                })
                const data = await res.json();
                console.log(data)
                this.listarUsuarios()
            }
            
        },
        created(){
            this.listarUsuarios();
        }
        
    }
</script>
