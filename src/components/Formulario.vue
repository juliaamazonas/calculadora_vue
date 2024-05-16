<script setup>

    

    const props = defineProps(['numero1', 'numero2', 'resultado', 'filtro']);

</script>

<template>
    <form>
        <div class="row">
            <div class="col">
                <input required placeholder="Número 1" @keyup="props.numero1" type="number"  class="form-control" id="numero1 ">
            </div>
            <div class="col">
                <input required placeholder="Número 2" @keyup="props.numero2" type="number"  class="form-control" id="numero2">
            </div>
            <div class="col-md-2">
                <select @change="props.filtro" class="form-control">
                    <option value="" disabled selected hidden>Operação</option>
                    <option value="adicao">Adição (+)</option>
                    <option value="subtracao">Subtração (-)</option>
                    <option value="multiplicacao">Multiplicação (*)</option>
                    <option value="divisao">Divisão (/)</option>
                </select>
            </div>
        </div>
        <div class="row">
            <div class="col">
                <p class="mt-3 bg-primary text-white"><br> Resultado: {{ props.resultado }} </p>
            </div>
        </div>
    </form>
</template>