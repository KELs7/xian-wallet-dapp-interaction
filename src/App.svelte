<script>
  import { onMount } from "svelte";
  import XianWalletUtils from "./xian-dapp-utils";
  
  let walletInfo;
  let balance;
  let dappUtils;

  onMount(async ()=>{
      XianWalletUtils.init();
        
      await requestWalletInfo();
      await updateBalance(); 
  });

  const requestWalletInfo = async()=> {
      walletInfo = await XianWalletUtils.requestWalletInfo();
  }

  const updateBalance = async() => {
     balance = await XianWalletUtils.getBalance("currency");
  }
  
</script>

<main>
  <button on:click={requestWalletInfo}>getWalletInfo</button>
  <button on:click={updateBalance}>getCurrentBalance</button>
  <p>address: {walletInfo?.address?walletInfo.address:"0x"}</p>
  <p>balance: {balance?balance: 0}</p>
  <p>chainId: {walletInfo?.chainId?walletInfo.chainId:"<chain-id>"}</p>
  <p>locked: {walletInfo?.locked}</p>
</main>

<style>
  
</style>
