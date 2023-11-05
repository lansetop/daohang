演示了如何通过SDK与Linea区块链进行交互,来实现账户查询,转账交易等功能。可以继续扩展更多应用。# daohang
daohang 
// 初始化
const { Linea } = require('@linea-network/sdk'); 

const linea = new Linea({
  // Linea网络节点
  endpoints: ['https://rpc.linea.network'], 
});

// 获取最新区块高度
async function getBlockNumber() {
  const blockNumber = await linea.chain.getBlockNumber();
  console.log(`Current block number: ${blockNumber}`);
}

// 获取账户余额 
async function getBalance(address) {
  const balance = await linea.chain.getBalance(address);
  console.log(`Balance of ${address}: ${balance}`); 
}

// 发送原生token转账
async function transfer(from, to, amount) {
  const tx = await linea.chain.transfer({
    from,
    to, 
    amount,
  });
  console.log(`Transaction hash: ${tx.hash}`);
} 

// 准备使用区块浏览器
const explorer = new Linea.Explorer();

// 获取交易信息
async function getTransaction(txHash) {
  const tx = await explorer.getTransaction(txHash); 
  console.log(tx);
}

// 更多网络查询API参考文档
