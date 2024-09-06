<script lang="ts">
    import Navbar from "../components/navbar.svelte";
    import { showEncuata } from "../stores/store";
    import { showCreateEncuesta } from "../stores/store";
    import a from "../../public/2279034.png";
    import b from "../../public/online-questions-and-answers-free-png.png";
    import c from "../../public/open-book-illustration-png.png";
import Capitule from "../components/capitule.svelte";
import{ shoCapiule } from "../stores/store";

    function toggEncuesta() {
        showEncuata.update((value) => !value);
    }
    function toggCreateEncuest() {
        showCreateEncuesta.update((value) => !value);
    }
    function toggCapitule(){
        shoCapiule.update(value => !value);
    }
</script>
<div class="fondos">
<Navbar />
<div class="dash fondo">
    <div class="input-group rounded">
        <input
            type="search"
            class="form-control rounded"
            placeholder="Search"
            aria-label="Search"
            aria-describedby="search-addon"
        />
        <span class="input-group-text border-0" id="search-addon">
            <i class="fas fa-search"></i>
        </span>
    </div>


            {#if !$showEncuata}
                <div class="options">
                    <a class="button" on:click={toggCreateEncuest}
                        >CREAR ENCUESTA</a
                    >
                    <a class="button">ELIMINAR ENCUESTA</a>
                    <a class="button">BUSCAR ENCUESTA</a>
                    <a on:click={toggEncuesta} class="button">Salir</a>
                </div>

                {#if !$showCreateEncuesta}
                    <form class="formulary p-4 bg-light border rounded">
                        <div class="form-group mb-3">
                            <label
                                for="exampleFormControlInput1"
                                class="form-label">Email address</label
                            >
                            <input
                                type="email"
                                class="form-control"
                                id="exampleFormControlInput1"
                                placeholder="name@example.com"
                            />
                        </div>

                        <div class="form-group mb-3">
                            <label
                                for="exampleFormControlSelect1"
                                class="form-label">Example select</label
                            >
                            <select
                                class="form-control"
                                id="exampleFormControlSelect1"
                            >
                                <option>1</option>
                                <option>2</option>
                                <option>3</option>
                                <option>4</option>
                                <option>5</option>
                            </select>
                        </div>

                        <div class="form-group mb-3">
                            <label
                                for="exampleFormControlSelect2"
                                class="form-label"
                                >Example multiple select</label
                            >
                            <select
                                multiple
                                class="form-control"
                                id="exampleFormControlSelect2"
                            >
                                <option>1</option>
                                <option>2</option>
                                <option>3</option>
                                <option>4</option>
                                <option>5</option>
                            </select>
                        </div>

                        <div class="form-group mb-3">
                            <label
                                for="exampleFormControlTextarea1"
                                class="form-label">Example textarea</label
                            >
                            <textarea
                                class="form-control"
                                id="exampleFormControlTextarea1"
                                rows="3"
                            ></textarea>
                        </div>
                        <a class="button" on:click={toggCapitule}>ECREAAR CAAPITLO</a>
                        {#if !$shoCapiule}
                            <Capitule/>
                        {/if}

                        <button type="submit" class="btn btn-primary">Submit</button>
                    </form>
                {/if}
                

      
            {/if}

            <div class="container mt-4" >
              <div class="row" >
                  <div class="col-md-4" on:click={toggEncuesta}>
                      <div class="card mb-4">
                          <img class="card-img-top" src={a} alt="Card image cap" />
                          <div class="card-body">
                              <h5 class="card-title">Encuestas</h5>
                          </div>
                      </div>
                  </div>
      

            <div class="col-md-4">
                <div class="card mb-4">
                    <img class="card-img-top" src={b} alt="Card image cap" />
                    <div class="card-body">
                        <h5 class="card-title">Resultados</h5>
                    </div>
                </div>
            </div>

            
            <div class="col-md-4">
              <div class="card mb-4">
                  <img class="card-img-top" src={c} alt="Card image cap" />
                  <div class="card-body">
                      <h5 class="card-title">Ajustes</h5>
                  </div>
              </div>
          </div>
        </div>
    </div>
</div>
</div>
<style lang="less">
    .fondos{  
/*           background-image: url('../../public/estrellas.jpg'); */ /* Coloca aquí la ruta de tu imagen */
   background: black;
/* background-size: cover; */ /* La imagen se ajusta para cubrir todo el contenedor */
/*     background-position: center; */ /* Centra la imagen en el contenedor */
    /* background-repeat: no-repeat; */ /* Evita que la imagen se repita */}
   
    .fondo {
    width: 300px;
    height: 200px;

    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    font-size: 18px;
    font-weight: bold;
}

    .options {
        z-index: 1000;
        position: absolute;
  /*       background: white; */
        margin: auto;
    }

    @col-primary: #00c7ec;
    @corner-radius: 5px;

    body {
        background-color: #012839;
        text-align: center;
        padding-top: 50px;
    }

    * {
        margin: 0;
        padding: 0;

    }

    .dash {
        height: 90vh;
        width: 100%;
        display: grid;
        align-items: center;
        justify-content: center;
    }

    .col-md-4 {
        padding: 15px;
    }

    .card {
        border: none;
        border-radius: 10px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        transition:
            transform 0.2s ease,
            box-shadow 0.2s ease;
        overflow: hidden;
    }

    .card:hover {
        transform: translateY(-5px);
        box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
    }

    .card-img-top {
        border-top-left-radius: 10px;
        border-top-right-radius: 10px;
        height: 200px;
        object-fit: cover;
    }

    .card-body {
        padding: 20px;
      /*   background-color: #f8f9fa; */
    }

    .card-title {
    font-size: 18px;
    font-weight: bold;
    margin-bottom: 10px;
    color: #333;
    display: flex;
    align-items: center; /* Corregido: 'align-itemscnet' a 'align-items: center' */
    text-align: center;
    justify-content: center; /* Corregido: 'ceneter' a 'center' */
}



    

    .btn-primary:active {
        background-color: #004080;
        transform: translateY(1px);
    }

    .btn-primary:focus {
        outline: none;
        box-shadow: 0 0 10px rgba(0, 123, 255, 0.5);
    }

    .formulary {
        z-index: 1000;
        height: 400px;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: auto;
    }

    .formulary .form-label {
        font-weight: 600;
        color: #495057;
    }

    .formulary .form-control {
        border-radius: 5px;
        border: 1px solid #ced4da;
        transition: border-color 0.3s ease;
    }

    .formulary .form-control:focus {
        border-color: #007bff;
        box-shadow: 0 0 0 0.2rem rgba(0, 123, 255, 0.25);
    }

    .formulary .form-group {
        margin-bottom: 1.5rem;
    }

    .options {
        display: flex;
        justify-content: center;
        gap: 20px;
        margin: 20px 0;
    }

    .button {
        display: inline-block;
        padding: 15px 25px;
        font-size: 16px;
        font-weight: bold;
        text-transform: uppercase;
        text-align: center;
        color: #fff;
        background-color: #007bff;
        border: none;
        border-radius: 5px;
        text-decoration: none;
        transition:
            background-color 0.3s ease,
            transform 0.2s ease;
    }

    .button:hover {
        background-color: #0056b3;
        transform: translateY(-3px);
    }

    .button:active {
        background-color: #004080;
        transform: translateY(1px);
    }

    .button:focus {
        outline: none;
        box-shadow: 0 0 10px rgba(0, 123, 255, 0.5);
    }
</style>
