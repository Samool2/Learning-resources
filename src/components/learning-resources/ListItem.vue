<template>
    <li>
        <base-card>
            <header>
                <h3>
                    {{title}}
                </h3>
            <base-button @click="removeResource(id)" class="flat">Delete</base-button>
                </header>
        <p>{{description}}</p>
        <nav>
        <a :href="link">View Resource</a>
        </nav>
        </base-card>
    
    </li>
</template>

<script>
    export default 
    {
        inject: ['removeResource'],
        props: ['id','title', 'description', 'link'],
        methods: {

            deleteMethod() {

            }



        }

    }
</script>

<style scoped>

button {
    float:right;
}
</style>