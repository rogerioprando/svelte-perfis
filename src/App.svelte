<script lang="ts">
    import Titulo from "./components/Titulo.svelte";
    import type IUsuario from "./interfaces/IUsuario";
    import Usuario from "./components/Usuario.svelte";
    import Formulario from "./components/Formulario.svelte";
    import Cabecalho from "./components/Cabecalho.svelte";

    // se "strictNullChecks": true temos que dizer pro compilador TS que usuarioApp pode ser nulo ou IUsuario
    let usuarioApp: IUsuario | null = null;

    function definirUsuario(evento: CustomEvent<IUsuario | null>){
        // Variável pai recebe os eventos que a variável filho ta enviando (Via dispatch)
        usuarioApp = evento.detail;
    }
</script>

<div>

    <Cabecalho on:aoAlterarUsuario={definirUsuario} />

    {#if usuarioApp}
        <!--
            Se o nome da váriavel usuario fosse igual a propriedade usuario do componente bastaria passar
            <Usuario {usuario} />
            Aqui está sendo passado uma prop de Pai (App) para Filho (Usuario)
        -->
        <Usuario usuario={usuarioApp}/>
    {/if}
</div>

<style>
    /* .app {
        max-height: 100vh;
    } */
</style>
