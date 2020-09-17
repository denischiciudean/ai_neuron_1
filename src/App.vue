<template>
    <div class="container">
        <div class="row">

            <div class="col-lg-12 text-center mt-5">
                <h1>NEURONI</h1>
            </div>

            <div class="col-lg-3">
                <div class="row">
                    <div class="col-lg-12">
                        Nr of inputs
                        <label>
                            <input type="number" v-model.number="input_count">
                        </label>
                    </div>
                    <div class="col-lg-12" v-for="n in input_count" v-bind:key="n">
                        <div class="row">
                            <div class="d-inline-block col-lg-2">{{n}}.</div>
                            <div class="d-inline-block col-lg-4">
                                <label>
                                    <input
                                            style="width: 50px;"
                                            type="text"
                                            @keyup="change_input_value(parseInt(n), $event.target.value) ">
                                </label>
                            </div>
                            <div class="d-inline-block col-lg-4">
                                <input
                                        style="width: 50px;"
                                        type="text"
                                        @keyup="change_input_weight_value(parseInt(n), $event.target.value) ">
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="col-lg-8">
                <div class="row">
                    <div class="col-lg-3">
                        <h3>Input Function</h3>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

    export default {
        name: 'App',
        data: function () {
            return {
                input_count: 4,
                inputs: {},
            }
        },
        methods: {
            change_input_value: function (n, value) {
                this.inputs[n] = {
                    ...this.inputs[n],
                    value: parseFloat(value)
                };
                console.log(this.inputs)
            },
            change_input_weight_value: function (n, value) {
                this.inputs[n] = {
                    weight: parseFloat(value),
                    ...this.inputs[n]
                };

            }
        }
    }
</script>
