<script>
  import { ethers } from "ethers";

  let state = false;
  if (window.ethereum) {
    state = true;
  } else {
    state = false;
  }

  let showTokenName = "...";
  let showTotalBalance = "...";
  let showAddress = 0;
  let showNetwork = "...";
  let provider;
  let ownerReady;
  let otherUser;
  let fmf;
  function handleClick(to) {
      ownerReady.transfer(to, fmf);
      console.log("1 FMF SENT TO "+ to);
    }

  if (state) {
    window.ethereum
      .enable()
      .then((provider = new ethers.providers.Web3Provider(window.ethereum)));

    window.ethereum
      .enable()
      .then((showAddress = window.ethereum.selectedAddress));

    provider.getNetwork().then((msg) => {
      showNetwork = msg.name;
    });

    const fmfAddress = "0xaa5c16e97906a14756e4a2bd0c14389c96509f5a";
    const fmfAbi = [
      {
        constant: true,
        inputs: [],
        name: "name",
        outputs: [
          {
            name: "",
            type: "string",
          },
        ],
        payable: false,
        stateMutability: "view",
        type: "function",
      },
      {
        constant: false,
        inputs: [
          {
            name: "spender",
            type: "address",
          },
          {
            name: "tokens",
            type: "uint256",
          },
        ],
        name: "approve",
        outputs: [
          {
            name: "success",
            type: "bool",
          },
        ],
        payable: false,
        stateMutability: "nonpayable",
        type: "function",
      },
      {
        constant: true,
        inputs: [],
        name: "totalSupply",
        outputs: [
          {
            name: "",
            type: "uint256",
          },
        ],
        payable: false,
        stateMutability: "view",
        type: "function",
      },
      {
        constant: false,
        inputs: [
          {
            name: "from",
            type: "address",
          },
          {
            name: "to",
            type: "address",
          },
          {
            name: "tokens",
            type: "uint256",
          },
        ],
        name: "transferFrom",
        outputs: [
          {
            name: "success",
            type: "bool",
          },
        ],
        payable: false,
        stateMutability: "nonpayable",
        type: "function",
      },
      {
        constant: true,
        inputs: [],
        name: "decimals",
        outputs: [
          {
            name: "",
            type: "uint8",
          },
        ],
        payable: false,
        stateMutability: "view",
        type: "function",
      },
      {
        constant: true,
        inputs: [],
        name: "_totalSupply",
        outputs: [
          {
            name: "",
            type: "uint256",
          },
        ],
        payable: false,
        stateMutability: "view",
        type: "function",
      },
      {
        constant: true,
        inputs: [
          {
            name: "tokenOwner",
            type: "address",
          },
        ],
        name: "balanceOf",
        outputs: [
          {
            name: "balance",
            type: "uint256",
          },
        ],
        payable: false,
        stateMutability: "view",
        type: "function",
      },
      {
        constant: true,
        inputs: [],
        name: "symbol",
        outputs: [
          {
            name: "",
            type: "string",
          },
        ],
        payable: false,
        stateMutability: "view",
        type: "function",
      },
      {
        constant: true,
        inputs: [
          {
            name: "a",
            type: "uint256",
          },
          {
            name: "b",
            type: "uint256",
          },
        ],
        name: "safeSub",
        outputs: [
          {
            name: "c",
            type: "uint256",
          },
        ],
        payable: false,
        stateMutability: "view",
        type: "function",
      },
      {
        constant: false,
        inputs: [
          {
            name: "to",
            type: "address",
          },
          {
            name: "tokens",
            type: "uint256",
          },
        ],
        name: "transfer",
        outputs: [
          {
            name: "success",
            type: "bool",
          },
        ],
        payable: false,
        stateMutability: "nonpayable",
        type: "function",
      },
      {
        constant: true,
        inputs: [
          {
            name: "a",
            type: "uint256",
          },
          {
            name: "b",
            type: "uint256",
          },
        ],
        name: "safeDiv",
        outputs: [
          {
            name: "c",
            type: "uint256",
          },
        ],
        payable: false,
        stateMutability: "view",
        type: "function",
      },
      {
        constant: false,
        inputs: [
          {
            name: "spender",
            type: "address",
          },
          {
            name: "tokens",
            type: "uint256",
          },
          {
            name: "data",
            type: "bytes",
          },
        ],
        name: "approveAndCall",
        outputs: [
          {
            name: "success",
            type: "bool",
          },
        ],
        payable: false,
        stateMutability: "nonpayable",
        type: "function",
      },
      {
        constant: true,
        inputs: [
          {
            name: "a",
            type: "uint256",
          },
          {
            name: "b",
            type: "uint256",
          },
        ],
        name: "safeMul",
        outputs: [
          {
            name: "c",
            type: "uint256",
          },
        ],
        payable: false,
        stateMutability: "view",
        type: "function",
      },
      {
        constant: true,
        inputs: [
          {
            name: "tokenOwner",
            type: "address",
          },
          {
            name: "spender",
            type: "address",
          },
        ],
        name: "allowance",
        outputs: [
          {
            name: "remaining",
            type: "uint256",
          },
        ],
        payable: false,
        stateMutability: "view",
        type: "function",
      },
      {
        constant: true,
        inputs: [
          {
            name: "a",
            type: "uint256",
          },
          {
            name: "b",
            type: "uint256",
          },
        ],
        name: "safeAdd",
        outputs: [
          {
            name: "c",
            type: "uint256",
          },
        ],
        payable: false,
        stateMutability: "view",
        type: "function",
      },
      {
        inputs: [],
        payable: false,
        stateMutability: "nonpayable",
        type: "constructor",
      },
      {
        payable: true,
        stateMutability: "payable",
        type: "fallback",
      },
      {
        anonymous: false,
        inputs: [
          {
            indexed: true,
            name: "from",
            type: "address",
          },
          {
            indexed: true,
            name: "to",
            type: "address",
          },
          {
            indexed: false,
            name: "tokens",
            type: "uint256",
          },
        ],
        name: "Transfer",
        type: "event",
      },
      {
        anonymous: false,
        inputs: [
          {
            indexed: true,
            name: "tokenOwner",
            type: "address",
          },
          {
            indexed: true,
            name: "spender",
            type: "address",
          },
          {
            indexed: false,
            name: "tokens",
            type: "uint256",
          },
        ],
        name: "Approval",
        type: "event",
      },
    ];
    const fmfContract = new ethers.Contract(fmfAddress, fmfAbi, provider);

    fmfContract.name().then((msg) => {
      showTokenName = msg;
    });

    fmfContract
      .balanceOf("0x751ae595f7a7dB174EfBa4BF45677E7A45aCeF06")
      .then((msg) => {
        showTotalBalance = ethers.utils.formatUnits(msg, 2);
      });

    const owner = new ethers.Wallet(
      "919bfb2b3e77765ae7c33b71f5b85db2979c6f0bb580b1cc7693e3c644dddf25",
      provider
    );

    fmf = ethers.utils.parseUnits("1.0", 2);
    ownerReady = fmfContract.connect(owner);
    otherUser = showAddress;

    window.ethereum.on("accountsChanged", function () {
      window.location.reload();
    });

    window.ethereum.on("chainChanged", (_chainId) => window.location.reload());

    window.ethereum.on("connect", function () {
      window.location.reload();
    });
  }
</script>

<main>
  <div
    class="bg-gradient-to-tr from-blue-300 to-green-300 min-h-screen flex-col flex items-center justify-center space-y-6"
  >
    {#if state === true}
      <div
        class="bg-gray-50 rounded-lg transition duration-500 ease-in-out shadow hover:shadow-2xl hover:bg-white p-4"
      >
        <p class="font-bold text-center text-xl">WELCOME</p>
        <p>Create your own currency just like the federal reserve!</p>
      </div>
      <div
        class="bg-gray-50 rounded-lg transition duration-500 ease-in-out shadow hover:shadow-2xl hover:bg-white p-4 m-4"
      >
        <p class="font-bold text-center text-xl">FMF</p>
        <p class="text-center">{showTokenName}</p>
        <p class="font-bold text-center text-xl">AVAILABLE SUPPLY</p>
        <p class="text-center">{showTotalBalance}</p>
        <p class="font-bold text-center text-xl">CONTRACT</p>
        <p class="text-center underline">
          <a
            href="https://ropsten.etherscan.io/address/0xaa5c16e97906a14756e4a2bd0c14389c96509f5a"
            >Link</a
          >
        </p>
      </div>
      <div class="flex flex-row items-center">
        <div
          class="bg-gray-50 rounded-lg transition duration-500 ease-in-out shadow hover:shadow-2xl hover:bg-white m-4"
        >
          <img
            class="h-48 w-48 object-scale-down"
            src="./img/eth.png"
            alt="Man looking at item at a store"
          />
        </div>
        <div
          class="bg-gray-50 rounded-lg transition duration-500 ease-in-out shadow hover:shadow-2xl hover:bg-white p-4"
        >
          <div class="flex flex-col items-center justify-center">
            <p class="font-bold text-center text-xl">ADDRESS</p>
            <p class="text-center">{showAddress}</p>
            <p class="font-bold text-center text-xl">NETWORK</p>
            <p class="text-center">{showNetwork}</p>
          </div>
        </div>
      </div>
      <button
        on:click={handleClick(otherUser)}
        class="rounded-full p-4 bg-purple-600 text-center text-lg visible text-white font-bold transition duration-500 ease-in-out shadow-2xl hover:shadow hover:bg-purple-500 focus:outline-none"
        >GET FMF</button
      >
    {:else}
      <div
        class="bg-gray-50 rounded-lg transition duration-500 ease-in-out shadow hover:shadow-2xl hover:bg-white p-4"
      >
        <p class="font-bold text-center text-xl">MetaMask not detected!</p>
        <p>
          Please install MetaMask to use this app: <a
            href="https://metamask.io/"
            class="underline">metamask.io</a
          >
        </p>
      </div>
    {/if}
  </div>
</main>

<style>
</style>
