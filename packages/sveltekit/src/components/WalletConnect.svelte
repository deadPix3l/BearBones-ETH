<script lang="ts">
    import { createWeb3Modal, defaultConfig } from '@web3modal/ethers'

    import {
    connected,
    provider,
    chainId,
    chainData,
    signer,
    signerAddress,
    contracts
} from "ethers-svelte";

// import { defaultEvmStores as evm } from "ethers-svelte";
	const projectId = "e31135fb502b9262b361a4251479cc48"
 
	// 2. Set chains
	const mainnet = {
	chainId: 1,
	name: 'Ethereum',
	currency: 'ETH',
	explorerUrl: 'https://etherscan.io',
	rpcUrl: 'https://cloudflare-eth.com'
	}

    const hardhat = {
        chainId: 31337,
        name: "Hardhat",
        currency: "ETH",
        explorerUrl: '/blockexplorer',
        rpcUrl: 'localhost:8545'
    }

	// 3. Create modal
	const metadata = {
	name: 'My Website',
	description: 'My Website description',
	url: 'https://mywebsite.com', // origin must match your domain & subdomain
	icons: ['https://avatars.mywebsite.com/']
	}

	const modal = createWeb3Modal({
	ethersConfig: defaultConfig({ metadata }),
	chains: [mainnet, hardhat],
	projectId,
	enableAnalytics: true // Optional - defaults to your Cloud configuration
	})

    function walletProvider() {
        console.log(modal.getWalletProvider())
    }

</script>

<w3m-network-button></w3m-network-button>
<w3m-button></w3m-button>

