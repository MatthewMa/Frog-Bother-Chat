<template>
    <div class="container">
        <Header></Header>
        <MessageView v-bind:messages="messages" v-bind:hench-men="henchMen"></MessageView>
        <Message v-bind:messages="messages"></Message>
    </div>
</template>

<script>
    // Imports
    import Header from "./components/Header";
    import MessageView from "./components/MessageView";
    import Message from "./components/Message";
    export default {
      name: 'app',
        components: {Message, MessageView, Header},
        // Change to Vuex in medium to large project
        data () {
            return {
                henchMen: ["Sonny", "Fredo", "Michael"],
                // Fake messages for poping up
                popMessages: ["Froggos have a little joke, that the world is so hard a man must have\n" +
                "two fathers to look after him, and that's why they have God Froggers.", "I'll make him an offer he can't refuse.",
                "The froggo with the long tongue can steal more flies than the man\n" +
                "with the gun.", "Please follow me.", "No one can beat me."],
                messages: {}
            }
        },
        methods: {
          generateMessages: function(){
            this.henchMen.forEach(item => {
                // Generate the number of messages randomly (3-5 messages)
                const number = Math.floor((Math.random() * 3) + 3);
                this.messages[item] = [];
                for (let i = 1; i <= number; i++) {
                    // Generate a random message
                    const message = this.popMessages[Math.floor(Math.random() * this.popMessages.length)];
                    this.messages[item].push({
                        content: message,
                        date: this.randomDate("1971-01-01", "2019-08-20")
                    });
                }
            });
          },
          // Generate a random date "yyyy-mm-dd" from "1971-01-01" to  "2019-08-20"
          randomDate: function(start, end) {
            var d = new Date(new Date(start).getTime() + Math.random() * (new Date(end).getTime() - new Date(start).getTime())),
                month = '' + (d.getMonth() + 1),
                day = '' + d.getDate(),
                year = d.getFullYear();

            if (month.length < 2) month = '0' + month;
            if (day.length < 2) day = '0' + day;

            return [year, month, day].join('-');
          }
        },
        created() {
          this.generateMessages();
        }
    }
</script>

<style lang="scss">

</style>
