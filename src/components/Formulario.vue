<template>

<div>
    <p>Componente de mensagem</p>
    <div>
        <form id="form-full">
            <div class="input-container">
                <label for="nome">Nome:</label>
                <input type="text" name="nome" id="nome" v-model="nome" placeholder="Digite seu nome">
            </div>
            <div class="input-container">
                <label for="carro">Carro:</label>
                <select name="carro" id="carro" v-model="carro">
                <option value="">Selecione seu carro</option>
                <option value="teste">Teste</option>
                </select>
            </div>
            <div class="input-container">
                <input type="submit" class="submit-btn" value="Cadastrar!">
            </div>
        </form>
    </div>
</div>
</template>

<script>
    export default{
        name: "Formulario",
    }


</script>

<style>
#form-full{
    max-width: 400px;
    margin: 0 auto;
}

.input-container{
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}

label{
    font-weight: bold;
    margin-bottom: 15px;
    color: #222;
    padding: 5px 10px;
    border-left: 4px solid #fcba03;
}

input, select{
    padding: 5px 10px;
    width: 300px;
}

.submit-btn{
    background-color: #222;
    color: #fcba03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: 0.5s;
}

.submit-btn:hover{
    background-color: transparent;
    color: #222;
}
</style>