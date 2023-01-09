<template>
    <div>
        <h3>Exemple sort</h3>
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
    }
}
</script>