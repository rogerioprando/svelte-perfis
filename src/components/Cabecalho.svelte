<script lang=ts>
    import Titulo from "./Titulo.svelte";
    import Formulario from "./Formulario.svelte";

</script>

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
    <Formulario on:aoAlterarUsuario/>

    </div>
</header>


<style>
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