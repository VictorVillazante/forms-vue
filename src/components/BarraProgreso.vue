<template>
    <h1 class="text-center">Progreso {{porcentajeCompletado}}%</h1>
    <div class="progress">
        <div class="progress-bar progress-bar-striped progress-bar-animated bg-success" role="progressbar"
            :aria-valuenow="porcentajeCompletado" aria-valuemin="0" aria-valuemax="100"
            :style="`width:${porcentajeCompletado}%`">

        </div>
    </div>
</template>

<script>
export default {
    props:["porcentajeCompletado"]
}
</script>

<style>

</style>