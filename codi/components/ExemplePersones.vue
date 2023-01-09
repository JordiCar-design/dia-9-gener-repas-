<template>
    <div>
        <div v-for="(persona, pos) in persones"
        :key="'persona'+pos"
        >
        {{ persona.nom }} - {{ persona.edat }}
        </div>
    </div>
</template>

<script>
export default{
    data(){
        return {
            persones:[
                {nom:'Jordi', edat:32},
                {nom:'Anna', edat:41},
                {nom:'Pere', edat:45}
            ]
        }
    }
}
</script>