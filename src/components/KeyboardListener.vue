
<!-- Waits for an event from Keyboard.vue
     and converts it to a Vue.js event -->

<script>

export default {
    name: 'KeyboardListener',
    emits: [
        'register-kb-listener', 'remove-kb-listener',
        'keydown', 'keyup', 'keypress'
    ],
    render() { return [] },
    created: function () {
        this.$emit('register-kb-listener', {
            id: this._uid,
            keydown: this.keydown,
            keyup: this.keyup,
            keypress: this.keypress
        })
    },
    beforeUnmount: function () {
        this.$emit('remove-kb-listener', {
            id: this._uid
        })
    },
    methods: {
        keydown (event) {
            this.$emit('keydown', event)
        },
        keyup (event) {
            this.$emit('keyup', event)
        },
        keypress (event) {
            this.$emit('keypress', event)
        },
    }
}

</script>
