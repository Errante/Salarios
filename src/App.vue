<template>
    <div id="contenedor">
        <div class="card">

            <h1>Tarifa</h1> <br>

            <select id="selector" class="form-select" v-model="categoria" aria-label="Default select example">

                <option selected>Categoria</option>
                <option value="1">1</option>
                <option value="2">2</option>
                <option value="3">3</option>

            </select> <br>

            <input class="input" type="text" v-model="horas"><br>

            <p></p>

            <button id="boton" type="button" class="btn btn-primary" @click="tarifa()">Aceptar</button> <br>

            <h4 id="resultado">{{ total }}</h4>

        </div>
    </div>
</template>

<script>

import { ref } from "vue";
export default {
    setup() {

        let horas = ref()
        let categoria = ref()
        let categoria1 = 12000
        let categoria2 = 17000
        let categoria3 = 22000
        let cuarenta = ref()
        let horasExtra = ref()
        let incremento = ref()
        let valorbase = ref()
        let extra = ref()
        let total = ref()

        function tarifa() {

            if (categoria.value == 1 && horas.value <= 40) {
                total.value = horas.value * categoria1
            }

            if (categoria.value == 2 && horas.value <= 40) {
                total.value = horas.value * categoria2
            }

            if (categoria.value == 3 && horas.value <= 40) {
                total.value = horas.value * categoria3
            }

            if (categoria.value == 1 && horas.value > 40) {
                cuarenta.value = 40 * categoria1
                horasExtra.value = horas.value - 40
                incremento.value = categoria1 * 0.25
                valorbase.value = categoria1 + incremento.value
                extra.value = horasExtra.value * valorbase.value
                total.value = cuarenta.value + extra.value
            }

            if (categoria.value == 2 && horas.value > 40) {
                cuarenta.value = 40 * categoria2
                horasExtra.value = horas.value - 40
                incremento.value = categoria2 * 0.25
                valorbase.value = categoria2 + incremento.value
                extra.value = horasExtra.value * valorbase.value
                total.value = cuarenta.value + extra.value
            }

            if (categoria.value == 3 && horas.value > 40) {
                cuarenta.value = 40 * categoria3
                horasExtra.value = horas.value - 40
                incremento.value = categoria3 * 0.25
                valorbase.value = categoria3 + incremento.value
                extra.value = horasExtra.value * valorbase.value
                total.value = cuarenta.value + extra.value
            }

        }

        return {

            horas, categoria, total, tarifa, horasExtra, incremento, extra,
            cuarenta, valorbase, categoria1, categoria2, categoria3

        }

    }

}



</script>

<style>
#cont {
    background-color: #30e920;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='100' height='100' viewBox='0 0 200 200'%3E%3Cdefs%3E%3ClinearGradient id='a' gradientUnits='userSpaceOnUse' x1='100' y1='33' x2='100' y2='-3'%3E%3Cstop offset='0' stop-color='%23000' stop-opacity='0'/%3E%3Cstop offset='1' stop-color='%23000' stop-opacity='1'/%3E%3C/linearGradient%3E%3ClinearGradient id='b' gradientUnits='userSpaceOnUse' x1='100' y1='135' x2='100' y2='97'%3E%3Cstop offset='0' stop-color='%23000' stop-opacity='0'/%3E%3Cstop offset='1' stop-color='%23000' stop-opacity='1'/%3E%3C/linearGradient%3E%3C/defs%3E%3Cg fill='%2300ca00' fill-opacity='0.6'%3E%3Crect x='100' width='100' height='100'/%3E%3Crect y='100' width='100' height='100'/%3E%3C/g%3E%3Cg fill-opacity='0.5'%3E%3Cpolygon fill='url(%23a)' points='100 30 0 0 200 0'/%3E%3Cpolygon fill='url(%23b)' points='100 100 0 130 0 100 200 100 200 130'/%3E%3C/g%3E%3C/svg%3E");
}

#contenedor {
    padding-top: 10%;
}

.card {
    padding-top: 20px;
    margin: 0 auto;
    border-radius: 20px;
    width: 350px;
    height: 400px;
    box-shadow: 10px 10px 10px rgb(0, 126, 0);
    text-align: center;
}

.form-select {
    border-radius: 20px;
    text-align: center;
    margin: 0 auto;
    width: 150px;
}

.input {
    text-align: center;
    border-radius: 30px;
    margin: 0 auto;
    width: 150px;
}

#boton {

    border-radius: 20px;
    margin: 0 auto;
}
</style>