<template>
    <Suspense>
        <template #default>
            <Home/>
        </template>
        <template #fallback>
            <SplashScreen/>
        </template>
    </Suspense>

</template>

<script>
//import Home from "@/components/Home.vue";
import SplashScreen from "@/components/SplashScreen.vue";
import { defineAsyncComponent } from "vue";
export default {
  components: {
    SplashScreen,
    Home: defineAsyncComponent(() =>
        new Promise((resolve) => {
            setTimeout(() => {
                resolve(import("./components/Home.vue"))

            }, 2500)
        })
    )
  },
};
</script>

<style>
html,
body,
.app {
  min-height: 100vh;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}
* {
  --brand-green: #dcd622;
  --brand-blue: #02151b;
}
</style>
