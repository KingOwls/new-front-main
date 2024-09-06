<script lang="ts">
    import { Link, navigate } from  'svelte-routing';
    import { showDashboar } from '../stores/store';
    import { axiosTools } from "../stores/store";
    import { onMount } from 'svelte';
    let user:String="";
    let password:string="";
    let token:any="";
   async function toggDashboard(){
if ( user =="" && password ==""){
    alert("Ingresar usuario y contraseña")
}else if (user =="")
{
    alert("ingresar usuario")
}else if (password ==""){
    alert("inresar contraseña")
}else{
    alert("ok")
    navigate("/DashBoard"); 

   try {
                const response = await fetch("http://localhost:8091/auth/login", {
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json",
                    },
                    body: JSON.stringify({ user, password }),
                });
                if (!response.ok) {
                    const errorData = await response.json();
                    console.error("Error:", errorData.message);
                    return;
                }
                const data = await response.json();
                if (data.token) {
                    token = data.token;
                    localStorage.setItem("token", token); 
                    console.log("JWT Token:", token);
                    navigate("/DashBoard"); 
                } else {
                    console.error("Token no encontrado en la respuesta");
                }
            } catch (error) {
                console.error("Error en la solicitud:", error);
            }
    }
}
onMount(() => {
        token = localStorage.getItem("token") || "";
    });


    
</script>

<div class="login">
    <input bind:value={user} placeholder="usuario" required>
    <input bind:value={password} placeholder="Contraseña" required>
    <p on:click={toggDashboard}>Entrar</p>
</div>

<style lang="less">
html, body {
    height: 100%; /* Asegúrate de que el body y html ocupen toda la altura */
    margin: 0; /* Elimina los márgenes por defecto */
}

.login {
    display: flex;
    flex-direction: column; /* Acomoda los elementos en columna */
    justify-content: center; /* Centra verticalmente */
    align-items: center; /* Centra horizontalmente */
    height: 100vh; /* Ocupa toda la altura de la ventana */
    width: 100vw; /* Ocupa toda la anchura de la ventana */
    margin: auto; /* Centra en caso de que haya otros márgenes */
    gap: 10px; /* Agrega espacio entre los elementos */
}

input {
    width: 200px;
    padding: 10px;
    font-size: 16px;
}

p {
    cursor: pointer;
    color: blue;
    font-size: 18px;
    text-align: center;
    margin-top: 10px;
}
</style>

