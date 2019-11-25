<template xmlns:v-model="http://www.w3.org/1999/xhtml">
    <div class="row" id="message_component">
        <div class="offset-2 col-md-8">
            <div class="input-group mb-3">
                <div class="input-group-prepend">
                    <span class="input-group-text" id="basic-addon1">@ {{currentSelectedPerson}}</span>
                </div>
                <input type="text" class="form-control" placeholder="Please input your message..." aria-label="message_input" aria-describedby="basic-addon1"
                v-model="inputMessage">
            </div>
        </div>
        <div class="col-md-2">
            <button type="button" class="btn btn-outline-secondary btn-block" :disabled="!inputMessage" v-on:click="sendMessage()">Send</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Message",
        props: {
            messages: {
                type: Object,
                required: true
            }
        },
        data() {
            return {
                inputMessage: "",
                currentSelectedPerson: "Sonny"
            }
        },
        methods: {
            sendMessage: function() {
                    // Add message
                    this.messages[this.currentSelectedPerson].push({
                        content: this.inputMessage,
                        date: this.getCurrentFormattedDate()
                    }
                );
            },
            /**
             * Get today formatted string
             * @returns {string|Date}
             */
            getCurrentFormattedDate: function () {
                var today = new Date();
                var dd = String(today.getDate()).padStart(2, '0');
                var mm = String(today.getMonth() + 1).padStart(2, '0'); //January is 0!
                var yyyy = today.getFullYear();
                today = yyyy + '-' + mm + '-' +dd;
                return today;
            }
        },
        created() {
            // Receive the change from MessageView component
            this.$root.$on('currentSelectedPersonChange', data => {
                this.currentSelectedPerson = data;
            });
        }
    }
</script>

<style scoped>
    #message_component {
        margin-top: 3%;
    }
</style>