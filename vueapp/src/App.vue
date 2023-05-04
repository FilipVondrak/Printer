<template>
    <div class="celek center">
        <h1>File Upload</h1>
        <input type="file" id="file" ref="file" v-on:change="handleFileUpload()">
        <button v-on:click="submitFile()">Submit</button>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        name: 'App',
        data() {
            return {
                file: null
            }
        },
        methods: {
            handleFileUpload() {
                this.file = this.$refs.file.files[0];
            },
            submitFile() {
                // Create a FormData object
                const formData = new FormData();
                formData.append('file', this.file);

                // Make a POST request to the backend
                axios.post('/api/Print', formData, {
                    headers: {
                        'Content-Type': 'multipart/form-data'
                    }
                })
            }
        }
    }
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }
    .celek {
        width: auto;
        padding: 30px;
        background: rgb(128, 128, 128);
    }
    .center {
        margin: 0;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
</style>
