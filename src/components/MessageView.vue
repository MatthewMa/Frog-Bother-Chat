<template>
    <div class="row" id="message_view">
        <div class="col-md-12">
            <div class="container-fluid">
                <div class="row">
                    <div class="col-md-4">
                        <div class="nav flex-column nav-pills" id="v-pills-tab" role="tablist" aria-orientation="vertical">
                            <!-- Dynamically generate in real App -->
                            <a class="nav-link active" data-toggle="pill" href="#v-pills-sonny" role="tab" aria-controls="v-pills-sonny" aria-selected="true" v-on:click="nameTabClick(henchMen[0])">{{henchMen[0]}}</a>
                            <a class="nav-link" data-toggle="pill" href="#v-pills-fredo" role="tab" aria-controls="v-pills-fredo" aria-selected="false" v-on:click="nameTabClick(henchMen[1])">{{henchMen[1]}}</a>
                            <a class="nav-link" data-toggle="pill" href="#v-pills-michael" role="tab" aria-controls="v-pills-michael" aria-selected="false" v-on:click="nameTabClick(henchMen[2])">{{henchMen[2]}}</a>
                        </div>
                    </div>
                    <div class="col-md-8">
                        <div class="tab-content" id="v-pills-tabContent">
                            <div class="tab-pane fade show active" id="v-pills-sonny" role="tabpanel" aria-labelledby="v-pills-sonny-tab">
                                <div class="card" v-for="sonnyMessage in sonnyMessages">
                                    <div class="card-header">
                                        {{sonnyMessage.date}}
                                    </div>
                                    <div class="card-body">
                                        <p class="card-text">{{sonnyMessage.content}}</p>
                                    </div>
                                </div>
                            </div>
                            <div class="tab-pane fade" id="v-pills-fredo" role="tabpanel" aria-labelledby="v-pills-fredo-tab">
                                <div class="card" v-for="fredoMessage in fredoMessages">
                                    <div class="card-header">
                                        {{fredoMessage.date}}
                                    </div>
                                    <div class="card-body">
                                        <p class="card-text">{{fredoMessage.content}}</p>
                                    </div>
                                </div>
                            </div>
                            <div class="tab-pane fade" id="v-pills-michael" role="tabpanel" aria-labelledby="v-pills-michael-tab">
                                <div class="card" v-for="michaelMessage in michaelMessages">
                                    <div class="card-header">
                                        {{michaelMessage.date}}
                                    </div>
                                    <div class="card-body">
                                        <p class="card-text">{{michaelMessage.content}}</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "MessageView",
        props: {
          messages: {
                type: Object,
                required: true
          }, henchMen: {
                type: Array,
                required: true
          }
        },
        data() {
            return {
              // Three messages for the tab contents
              sonnyMessages: [],
              fredoMessages: [],
              michaelMessages: []
            };
        },
        methods: {
            nameTabClick: function (currentHenchMan) {
                // Send event to notify the change
                this.$root.$emit('currentSelectedPersonChange', currentHenchMan);
            }
        },
        created() {
            this.sonnyMessages = this.messages["Sonny"];
            this.fredoMessages = this.messages["Fredo"];
            this.michaelMessages = this.messages["Michael"];
        }
    }
</script>

<style scoped>
    #message_view {
        margin-top: 10%;
    }
    #v-pills-tab a {
        margin-top: 5%;
    }
    #v-pills-tab a {
        background-color: #CDCDCD;
        color: black;
        font-weight: bolder;
        text-align: center;
    }
    #v-pills-tab a.active {
        background:#4FA9DC;
        color:white;
    }
    #v-pills-tabContent {
        min-height: 800px;
        background-color: #f1f1f1;
        border: black 1px;
        border-radius: 5px;
    }
    .card-header {
        background-color: #4FA9DC;
        color: white;
        font-weight: bolder;
    }
    .card {
        margin-bottom: 4%;
    }
</style>