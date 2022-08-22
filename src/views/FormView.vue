<template>
    <div class="flex w-full pt-12 justify-center items-center">
        <div class=" flex flex-col md:flex-row md:space-x-6 space-y-6  md:space-y-0 bg-gray-800 w-full max-w-6xl p-8  rounded-xl shadow-lg text-white">
            
            <div class="flex flex-1 flex-col space-y-8 justify-around	  " >
                <div class="text-left">
                    <h1 class="font-bold text-4xl tracking-wide">Prodequa</h1>
                    <p class="pt-2 text-sm">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Officia, exercitationem dolorum? Obcaecati voluptate distinctio sit qui sapiente voluptatem ex repellendus assumenda, libero molestiae et aut ab quo molestias eius. Veniam.
                    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Et voluptatum explicabo laudantium iusto molestiae, numquam commodi natus modi maxime tempore quasi, quod sit, sapiente enim accusamus adipisci fugiat dolorem ea.</p>
                </div>
                <div class="flex flex-col space-y-4">
                    <div class="inline-flex space-x-2 items-center">
                        <span >(+51) 988 250 642</span>
                    </div>
                    <div class="inline-flex space-x-2 items-center">
                        <span >soluciones@prodequa.com</span>
                    </div>
                    <div class="inline-flex space-x-2 items-center">
                        <span >Calle Gral. Belisario Suárez 518</span>
                    </div>
                </div> 
            </div>
            
            <div class="bg-gray-900 rounded-xl shadow-lg p-8 space-x-8 flex-1 " >
                <form @submit.prevent="registerUser" class="flex flex-col space-y-4">
                    <div>
                        <input 
                            type="text" 
                            v-model="task.usuario"
                            placeholder="Nombre y Apellido" 
                            class=" w-full px4 py-2 outline-none bg-transparent border-0  border-b-2 focus:b">
                    </div>
                    <div>
                        <input 
                            type="text" 
                            v-model="task.razonSocial"
                            placeholder="Razon Social"
                            class=" w-full px4 py-2 outline-none bg-transparent border-0  border-b-2">
                    </div>
                    <div>
                        <input 
                            type="text" 
                            v-model="task.cargo"
                            placeholder="cargo"
                            class=" w-full px4 py-2 outline-none bg-transparent border-0  border-b-2">
                    </div>
                    <div>
                        <input 
                            type="number" 
                            v-model="task.celular"
                            placeholder="celular"
                            class=" w-full px4 py-2 outline-none bg-transparent border-0  border-b-2">
                    </div>
                    <div>
                        <input 
                            type="email" 
                            v-model="task.correo" 
                            placeholder="Correo"
                            class=" w-full px4 py-2 outline-none bg-transparent border-0  border-b-2">
                    </div>
                    <div>
                        <textarea 
                        v-model="task.mensaje"  
                        cols="30" 
                        rows="10" 
                        placeholder="Mensaje"
                        class=" w-full px4 py-2 outline-none bg-transparent border-0  border-b-2 max-h-52 min-h-full" ></textarea>
                    </div>
                     <div>
                        <button class="inline-block self-end bg-white text-black font-bold rounded-lg px-6 py-2 uppercase text-sm "> Enviar</button>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>

    class usuario {
        constructor(usuario,razonSocial,cargo,celular,correo,mensaje){
            this.usuario = usuario
            this.razonSocial = razonSocial
            this.cargo = cargo
            this.celular = celular
            this.correo = correo
            this.mensaje = mensaje
        }
    }

    export default {
        data(){
            return{
                task: new usuario(),
            }
        },
        methods:{
            async registerUser(){
                const res = await fetch('https://api-expre.herokuapp.com/api/formulario',{
                        method : 'POST',
                        body : JSON.stringify(this.task),
                        headers : {
                            'Accept': 'application/json',
                            'Content-type':'application/json'
                        }   
                    });
                const data = res.json(res);
                console.log(data)
                this.task = new usuario()
            }
        }
    }
</script>
