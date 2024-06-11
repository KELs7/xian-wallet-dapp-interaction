<script>
  import { onMount } from "svelte";
  import { XianWalletUtils } from "./xian-dapp-utils";
  
  let walletInfo;
  onMount(()=>{
      XianWalletUtils.init();
  });
  
  const requestWalletInfo = async()=> {
      walletInfo = await XianWalletUtils.requestWalletInfo();
  }

</script>

<main>
  <button on:click={requestWalletInfo}>getWalletInfo</button>
  <p>address: {walletInfo?.address?walletInfo.address:"0x"}</p>
  <p>chainId: {walletInfo?.chainId?walletInfo.chainId:"<chain-id>"}</p>
  <p>locked: {walletInfo?.locked}</p>
</main>

<style>
  
</style>
