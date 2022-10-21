<script lang="ts">
    import Titulo from "./components/Titulo.svelte";
    import type IUsuario from "./interfaces/IUsuario";
    import Usuario from "./components/Usuario.svelte";
    import Formulario from "./components/Formulario.svelte";

    // se "strictNullChecks": true temos que dizer pro compilador TS que usuarioApp pode ser nulo ou IUsuario
    let usuarioApp: IUsuario | null = null;

    function definirUsuario(evento: CustomEvent<IUsuario>){
        // Variável pai recebe os eventos que a variável filho ta enviando (Via dispatch)
        usuarioApp = evento.detail;
    }
</script>

<div>
    <header>
        <Titulo />

        <div class="busca-usuario">
            <!--
                USANDO BIND:
                Aqui precisamos fazer bind pois queremos que a prop Filho (Formulario) passe pro Pai (App)
                Se as variáveis dos componentes possuisseem mesmo nome (usuario) basta deixar assim
                <Formulario bind:usuario />
                <Formulario bind:usuarioForm={usuarioApp} />
            -->
            <!-- 
                USANDO DISPATCH
            -->
        <Formulario on:aoAlterarUsuario={definirUsuario}/>
        </div>
    </header>

    {#if usuarioApp}
        <!--
            Se o nome da váriavel usuario fosse igual a propriedade usuario do componente bastaria passar
            <Usuario {usuario} />
            Aqui está sendo passado uma prop de Pai (App) para Filho (Usuario)
        -->
        <Usuario usuario={usuarioApp} />
    {/if}
</div>

<style>
    /* .app {
        max-height: 100vh;
    } */

    header {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .busca-usuario {
        position: relative;
        width: 70%;
    }
</style>
