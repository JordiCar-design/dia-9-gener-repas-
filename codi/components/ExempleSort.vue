<template>
    <div>
        <h3>Exemple sort</h3>
        <v-btn @click="ordenarDescendent()">
        ordenar Descendent
        </v-btn>
        <v-btn @click="ordenarAscendent()">
            ordenar Ascendent

        </v-btn>
        <pre>
            {{ edats }}
        </pre>
    </div>
</template>

<script>
export default{
    mounted(){
        const nums = [10, 5, 8, 1, 7]

        nums.sort(

            (a, b) => {
                return a - b
            }
        )

        console.log(nums) // [1, 10, 5, 7, 8]
        this.edats = nums
    },
    data(){
        return {
            // Estat del component
            edats: null
        }
    },
    methods:{
        ordenarDescendent(){
            this.edats.sort(
                (a, b)=> {
                    console.log(a,b)
                    return b - a 
                },
            )
        },
        ordenarAscendent(){
            let contador = 0
            this.edats.sort(
                    (a, b)=> {
                        console.log(a,b)
                        contador--
                        return a - b
                }
            )
            console.log("S'ha executat "+contador+" cops")
        }
    }
}
</script>