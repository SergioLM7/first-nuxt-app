<template>
    <div>

        <div>
            <img v-if="statusCode === 503" src="../static/images/503image.jpg" alt="503 message" />
            <img v-else-if="statusCode === 404" src="../static/images/404image.jpg" alt="404 message" />
        </div>

        <div class="title">
            {{ message }}
        </div>
        <p v-if="statusCode === 404">
            <nuxt-link to="/">
                Return to homepage
            </nuxt-link>
        </p>
    </div>
</template>

<script>
export default {
    props: {
        error: {
            type: Object,
            default: null
        }
    },
    head() {
        return {
            title: this.message
        }
    },
    computed: {
        statusCode() {
            return (this.error && this.error.statusCode) || 500
        },
        message() {
            return this.error.message
        }
    }
}
</script>