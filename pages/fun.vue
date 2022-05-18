<template>
    <div >
        <h1>
            About this app.
        </h1>
        <p>This is sample nuxt app.</p>
    </div>
</template>

<script>
export default {
    head(){
        return  {
            title: "fun nuxt app.",
            meta:[
                {
                    hid:'decription',
                    name:'descriotion',
                    content:'best place will sample app'
                }
            ]
        }
    }
}
</script>