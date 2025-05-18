# 🌀 Chainlink Cross-Chain NFT Transfer

![Chainlink CCIP Logo](https://docs.chain.link/img/ccip/ccip-diagram.png)

## 🚀 Giới thiệu

**Chainlink Cross-chain NFT Transfer** là một DApp mẫu minh họa cách sử dụng **Chainlink CCIP (Cross-Chain Interoperability Protocol)** để **gửi và nhận NFT giữa các chuỗi khối khác nhau** một cách an toàn và không cần niềm tin. Dự án này cho thấy cách xây dựng các ứng dụng NFT có thể tương tác xuyên chuỗi mà không cần viết nhiều smart contract riêng biệt cho từng chain.

## 🔧 Tính năng chính

* Gửi NFT từ Chain A sang Chain B thông qua Chainlink CCIP
* Nhận NFT ở chain đích với đầy đủ metadata
* Hỗ trợ mã hóa/giải mã dữ liệu NFT gửi đi
* Giao diện Web3 thân thiện
* Hiển thị lịch sử chuyển NFT xuyên chuỗi

---

## 🏗️ Kiến trúc hệ thống

```plaintext
Chain A (Source)           Chainlink CCIP            Chain B (Destination)
+------------------+       +-------------+          +---------------------+
| NFT Contract     | <---> | CCIP Router | <------> | NFT Receiver        |
| CCIP Sender      |       +-------------+          | CCIP Receiver       |
+------------------+                                +---------------------+

                    👇 Giao diện Web3 (Frontend)
                React/Next.js + Wagmi + Viem + Ethers
```

---

## 📁 Cấu trúc thư mục

```bash
.
├── contracts/                              # Hợp đồng thông minh
│   ├── ChainlinkCrossNFT.sol               # ERC-721 NFT contract
│   ├── SourceMinter.sol                    # Gửi dữ liệu xuyên chuỗi
│   └── DestinationMinter.sol               # Nhận dữ liệu xuyên chuỗi
├── frontend/                 # Giao diện người dùng
│   ├── pages/
│   ├── components/
│   └── utils/
├── scripts/                  # Script deploy và tương tác
├── test/                     # Kiểm thử smart contract
├── hardhat.config.ts
├── README.md
└── package.json
```

---

## 🧪 Yêu cầu hệ thống

* Node.js >= 18
* Hardhat / Foundry
* Chainlink CCIP SDK
* Metamask hoặc ví hỗ trợ testnet
* Chain A/B: Sepolia, Avalanche Fuji, Optimism Goerli (tuỳ chọn)

---

## 🔨 Hướng dẫn cài đặt và chạy demo

### 1. Clone repo

```bash
git clone https://github.com/songonha/cross-chain-nft-transfer.git
cd cross-chain-nft-transfer
```

### 2. Cài đặt dependencies

```bash
npm install
# hoặc
yarn install
```

### 3. Cấu hình môi trường `.env`

Tạo file `.env` và thêm thông tin:

```env
PRIVATE_KEY=your_wallet_private_key
RPC_URL_SEPOLIA=https://...
RPC_URL_AVALANCHE=https://...
CCIP_ROUTER_SEPOLIA=0x...
CCIP_ROUTER_AVALANCHE=0x...
NFT_CONTRACT_ADDRESS=0x...
```

> Bạn có thể tìm địa chỉ Router CCIP tại: [https://docs.chain.link/ccip/supported-networks](https://docs.chain.link/ccip/supported-networks)

---

### 4. Deploy contract

```bash
npx hardhat run scripts/deploy-nft.ts --network sepolia
npx hardhat run scripts/deploy-ccip.ts --network sepolia
```

Làm tương tự cho mạng đích như Avalanche Fuji.

---

### 5. Chạy frontend

```bash
cd frontend
npm run dev
```

---

## 📷 Giao diện minh họa

| Chức năng          | Hình ảnh                       |
| ------------------ | ------------------------------ |
| Trang gửi NFT      | ![](./screenshots/send.png)    |
| Trang nhận NFT     | ![](./screenshots/receive.png) |
| Lịch sử chuyển NFT | ![](./screenshots/history.png) |

---

## 🛡️ Bảo mật & Giới hạn

* Tích hợp CCIP Gas Fee thanh toán bằng LINK
* Kiểm tra chainId để chỉ cho phép gửi tới các chuỗi được hỗ trợ
* Giới hạn chỉ chủ NFT mới có thể gửi
* Hợp đồng receiver xác thực nguồn CCIP message

---

## 📚 Tài liệu tham khảo

* [Chainlink CCIP Overview](https://docs.chain.link/ccip)
* [Cross-chain NFT Example](https://github.com/smartcontractkit/ccip-cross-chain-nft)
* [ERC721 Standard](https://eips.ethereum.org/EIPS/eip-721)

---

## 💡 Đóng góp

Mọi đóng góp đều được hoan nghênh! Hãy mở Pull Request hoặc Issue để cùng xây dựng hệ thống NFT xuyên chuỗi an toàn và hiệu quả.

---

## ⚖️ Giấy phép

MIT License

---
