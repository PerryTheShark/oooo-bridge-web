<template>
    <OContainer>
            
            <OHeader class="flex md:flex-row md:items-center md:justify-start" title="_ REWARDS HUB"> 
                <div class="flex flex-col md:flex-row md:items-center mt-[20px] md:mt-0 md:mr-auto">
                    <p class="mr-[8px] text-[14px] md:text-base text-[#a4a4a4] -tracking-tighter">YOUR ACCOUNT: </p>
                    <WalletConnectButton />
                </div>
                
            </OHeader>

    </OContainer> 
</template>

<script setup lang="ts">
    import { OContainer, OHeader } from '@/components/OContainer'
    import WalletConnectButton from 'D:/Fatpay/oooo-bridge-web/src/components/layout/WalletConnectButton.vue'

</script>

<style scoped>
h1 {
  color: #42b983;
}
</style>
