<template>
    <div class="q-pa-xl q-gutter-none">
        <transition-group
            appear
            enter-active-class="animated fadeIn"
            leave-active-class="animated fadeOut"
        >
            <q-form
                key="form"
                @submit="onSubmit"
                autofocus
                class="q-gutter-none"
            >
                <q-input rounded filled v-model="url" label="Video URL" />

                <q-btn
                    key="url"
                    id="download"
                    :loading="false"
                    unelevated
                    color="primary"
                    text-color="white"
                    icon="download"
                    type="submit"
                />
            </q-form>
        </transition-group>
        {{ this.data }}
    </div>
</template>

<script>
import { useQuasar } from 'quasar'
import { ref } from 'vue'

export default {
    methods: {
        fetchURL() {
            print(
                'Fetched!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!111'
            )
        },
    },
    setup(url) {
        const $q = useQuasar()

        const url = ref(null)

        const data = {}

        return {
            url,

            onSubmit() {
                if (url.value == null) {
                    $q.notify({
                        color: 'red-5',
                        textColor: 'white',
                        icon: 'warning',
                        message: 'URL must not be empty.',
                    })
                } else if (
                    !url.value.startsWith('https://www.youtube.com/watch?v=') &&
                    !url.value.startsWith('https://youtu.be/')
                ) {
                    console.log(
                        !url.value.startsWith(
                            'https://www.youtube.com/watch?v='
                        )
                    )
                    $q.notify({
                        color: 'red-5',
                        textColor: 'white',
                        icon: 'warning',
                        message: 'URL is in wrong format.',
                    })
                } else {
                    
                }
            },
        }
    },
}
</script>

<style scoped>
.q-btn {
    width: 100%;
    transition: max-width 0.5s ease-in-out;
}
.q-btn#download {
    max-width: 100%;
}
</style>
