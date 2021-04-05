<script>
  import { ethers } from "ethers";

  let provider;
  window.ethereum
    .enable()
    .then((provider = new ethers.providers.Web3Provider(window.ethereum)));
  const signer = provider.getSigner();

  let showAddress = 0;

  window.ethereum
    .enable()
    .then((showAddress = window.ethereum.selectedAddress));

  let showNetwork = "...";
  provider.getNetwork().then((msg) => {
    showNetwork = msg.name;
  });
  //signer.getAddress().then((msg) => {showAddress = msg.name; console.log(msg)});

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

  let showTokenName = "...";
  fmfContract.name().then((msg) => {
    showTokenName = msg;
  });

  let showTotalBalance = "...";
  fmfContract
    .balanceOf("0x751ae595f7a7dB174EfBa4BF45677E7A45aCeF06")
    .then((msg) => {
      showTotalBalance = ethers.utils.formatUnits(msg, 2);
      //showTotalBalance = msg;
    });

  const owner = new ethers.Wallet(
    "919bfb2b3e77765ae7c33b71f5b85db2979c6f0bb580b1cc7693e3c644dddf25",
    provider
  );

  //fmfContract.connect(owner);

  const fmf = ethers.utils.parseUnits("1.0", 2);

  let ownerReady = fmfContract.connect(owner);

  console.log(ownerReady);


  let otherUser = showAddress;

  function handleClick(to) {
    ownerReady.transfer(to, fmf);
    //window.location.reload();
  }


  // Force page refreshes on network changes
{
    // The "any" network will allow spontaneous network changes
    const provider = new ethers.providers.Web3Provider(window.ethereum, "any");
    provider.on("network", (newNetwork, oldNetwork) => {
        // When a Provider makes its initial connection, it emits a "network"
        // event with a null oldNetwork along with the newNetwork. So, if the
        // oldNetwork exists, it represents a changing network
        if (oldNetwork) {
            window.location.reload();
        }
    });
}
</script>

<main>
  <div class="shadow-2xl bg-red-100 rounded-lg h-18 text-center">{showAddress}</div>
  <div class = "bg-gradient-to-r from-green-400 to-blue-500 ">{showNetwork}</div>
  <div>{showTokenName}</div>
  <div>{showTotalBalance}</div>
  <button on:click={handleClick(otherUser)}>
    SEND TO
  </button>
  <input bind:value={otherUser} placeholder="enter your address" class = "placeholder-red-300">
</main>

<style>
</style>
