<template>
    <div>
        <div v-for="(persona, pos) in persones" :key="'persona' + pos">
            {{ persona.nom }} - {{ persona.edat }}
        </div>
        <div>
            <v-text-field v-model="nom" label="nom"></v-text-field>
            <v-text-field v-model="nom" label="edat"></v-text-field>
        </div>
        <div>
            <v-btn @click="ordenarAZ()">a to z</v-btn>
            <v-btn @click="ordenarZA()">z to a</v-btn>
            <v-btn @click="ordenarEdatAsc()">Edat Ascendent</v-btn>
            <v-btn @click="ordenarEdatDesc()">Edat Descendent</v-btn>

            <br>
            Edat més gran: {{ edatMesGran }} anys
            <br>
            Edat més petita: {{ edatMesPetita }} anys
            <br>
            Mitjana d'edat: {{ edatMitjana }}

        </div>

        <!-- <div> 
            <v-btn @click="ordenarAZ()">a to z</v-btn>
            <v-btn @click="ordenarZA()">z to a</v-btn>
        </div>
        <div>
            <v-btn @click="edatAsc()">edat ascendent</v-btn>
            <v-btn @click="edatDesc()">edat descendent</v-btn>
        </div>-->

    </div>
    <!-- Creant els botons en divs diferents, un queda a sota 
    de l'altre mentre que en el mateix div queden de costat -->
</template>

<script>
export default {
    data() {
        return {
            persones: [
                { nom: 'Jordi', edat: 32 },
                { nom: 'Anna', edat: 41 },
                { nom: 'Pere', edat: 45 }
            ]
        }
    },
    methods: {
        afegeixHttps(url) {
            return "https://" + url
        },
        ordenarAZ() {
            this.persones.sort(
                (a, b) => {
                    if (a.nom < b.nom) return -1;
                    if (a.nom > b.nom) return 1;
                    return 0;
                }
            )
        },
        ordenarZA() {
            this.persones.sort(
                (a, b) => {
                    if (a.nom > b.nom) return -1;
                    if (a.nom < b.nom) return 1;
                    return 0;
                }
            )
        },
        edatAsc() {
            this.persones.sort(
                (a, b) => {
                    if (a.edat > b.edat) return -1;
                    if (a.edat < b.edat) return 1;
                    return 0;
                }
            )
        },
        edatDesc() {
            this.persones.sort(
                (a, b) => {
                    if (a.edat < b.edat) return -1;
                    if (a.edat > b.edat) return 1;
                    return 0;
                }
            )
        }
    },
    computed: {
        edatMesGran() {
            let maxim = -Infinity

            this.persones.forEach(
                function (persona, posicio, array) {
                    if (persona.edat > maxim) {
                        maxim = persona.edat
                    }
                }
            )
        },
        edatMesPetita() {
            let minim = Infinity

            this.persones.forEach(
                function (persona, posicio, array) {
                    if (persona.edat < minim) {
                        minim = persona.edat
                    }
                }
            )
            return minim
        },
        edatMitjana() {
            let totalEdats = 0

            this.persones.forEach(
                (persona, posicio, array) => {
                    totalEdats += persona.edat
                }
            )
            return totalEdats / this.persones.length
        }
    }
}
</script>