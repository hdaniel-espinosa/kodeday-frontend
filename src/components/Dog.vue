<template>
    <article class="pet">
        <div class="pet-container">
            <div class="pet-image">
                <figure class="image">
                    <img 
                    :src="imageSrc"
                    >
                </figure>
            </div>
            <div class="pet-detail">
                <h6 class="pet-name">
                    {{ "Nombre: " +  name }}
                </h6>
                <p class="pet-description">
                    {{ "Edad: " + age }}, {{ "Genero: " + gender }}, {{ "Raza: " + breed }}, {{ "Adoptado: " + isAdopted}}
                </p>
            </div>
        </div>

        <footer class="pet-options">
            <Button
            text="Adoptar"
            class="green"
            @click="adopt"
            />
            <Button
            text="Borrar"
            class="red"
            />
        </footer>
    </article>
</template>

<script>
    import Button from './Button'

    export default {
        name: 'Dog',
        props: {
            imageSrc: {
                type: String,
                default: ''
            },
            id: {
                type: Number,
                default: null
            },
            name: {
                type: String,
                default: ''
            },
            age: {
                type: Number,
                default: null
            },
            breed: {
                type: String,
                default: ''
            },
            gender: {
                type: String,
                default: ''
            },
            isAdopted: {
                type: Number,
                default: null
            }
        },
        components: {
            Button
        },
        methods: {
            async adopt() {
                const response = await fetch(`https://dogapi-59p4hrc7v.now.sh/dogs/${this.id}`, {
                    method: 'PUT'
                })
                const data = await response.json()

                alert(data.message)
                alert('adoptado!')

                this.$emit('dog-adopted', this.id)
            }
        }
    }
</script>

<style scoped></style>