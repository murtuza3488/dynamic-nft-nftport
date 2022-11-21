## Follow steps to create Dynamic NFT

### Step 1: Deploy your contract
#### API
**POST** `https://api.nftport.xyz/v0/contracts`

####  Headers
`Authorization`: <Your API key>
`Content-Type`: `application/json`

#### Request
`{   
  chain: "polygon",
  name: "Dynamic Island",
  symbol: "DI",
  owner_address: "Your wallet address here",
  metadata_updatable: true
}`

### Step 2: Get the contract address
#### API
**GET** `https://api.nftport.xyz/v0/contracts/transaction_hash`

####  Headers
`Authorization`: <Your API key>
`Content-Type`: `application/json`
`chain`: `polygon`

### Step 3: Upload your assets
#### API
**POST** `https://api.nftport.xyz/v0/files`

####  Headers
`Authorization`: <Your API key>
`Content-Type`: `multipart/form-data`

#### Formdata Body
`file`: `@/path/to/file_to_upload.png;type=image/png`

### Step 4: Create and Upload the metadata
#### API
**POST** `https://api.nftport.xyz/v0/metadata`

####  Headers
`Authorization`: <Your API key>
`Content-Type`: `application/json`

#### Request
`{
  "name": "Your NFT name",
  "description": "Your NFT description",
  "file_url": "The ipfs_url you got from the previous request response"
}`

### Step 5: Create and Upload the metadata
#### API
**POST** `https://api.nftport.xyz/v0/mints/customizable`

####  Headers
`Authorization`: <Your API key>
`Content-Type`: `application/json`

#### Request
`{
  "chain": "polygon",
  "contract_address": "The contract address which you got from step 1 A",
  "metadata_uri": "Metadata URI for Initial State",
  "mint_to_address": "Account address where the NFT will be sent."
}`

### Step 6: Get the Token ID
#### API
**GET** `https://api.nftport.xyz/v0/mints/{transaction_hash}`

####  Headers
`Authorization`: <Your API key>
`Content-Type`: `application/json`
`chain`: `polygon`


### Step 7: Update Metadata
#### API
**PUT** `https://api.nftport.xyz/v0/mints/customizable`
 
####  Headers
`Authorization`: <Your API key>
`Content-Type`: `application/json`

#### Request
`{
  "chain": "polygon",
  "contract_address": "The deployed contract address.",
  "token_id": "The token ID which you got from step 6",
  "metadata_uri": "The new metadata uri with which you want your NFT to be linked"
}`