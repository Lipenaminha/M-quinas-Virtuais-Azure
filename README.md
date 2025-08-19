As máquinas virtuais (VM) do Azure podem ser criadas por meio do **Portal do Azure**.  
Esse início rápido mostra como implantar uma **VM Windows Server 2022 Datacenter** e habilitar **RDP** + instalar **IIS**.

---

## 🔑 Entrar no Azure
1. Acesse o portal: [https://portal.azure.com](https://portal.azure.com)  
2. Faça login com sua conta Azure.  

---

## 🚀 Criar a máquina virtual
1. No portal, pesquise **Máquinas virtuais**.  
2. Clique em **Criar** → **Máquina virtual do Azure**.  
3. Em **Detalhes da instância**:
   - Nome: `myVM`  
   - Imagem: **Windows Server 2022 Datacenter: Azure Edition - x64 Gen 2**  
   - Região: escolha uma próxima de você  
   - Tamanho: mantenha o padrão  
   - ![Detalhes da instância](instance-details.png)  

> ℹ️ Alguns usuários verão a opção de criar VMs em zonas de disponibilidade.  

4. Em **Conta de administrador**:
   - Usuário: `azureuser`  
   - Senha: mínimo 12 caracteres + complexidade  
   - ![Conta de administrador](/images/azure-vm-admin.png)  

5. Em **Regras de porta de entrada**:
   - Selecione **Permitir portas selecionadas**  
   - Ative **RDP (3389)** e **HTTP (80)**  
   - ![Regras de porta](/images/azure-vm-networking.png)  

6. Clique em **Examinar + criar** → depois em **Criar**.  
   - ![Review + Create](/images/azure-vm-review.png)  

7. Após a validação, clique em **Criar**.  

---

## 🔗 Conectar-se à máquina virtual
1. No portal → abra sua VM.  
2. Clique em **Conectar** → **RDP**.  
3. Baixe o arquivo `.rdp`.  
4. Abra-o e clique em **Conectar**.  
5. Na tela de login:  
   - Usuário: `localhost\\azureuser`  
   - Senha: definida na criação da VM  
6. Ignore o aviso de certificado clicando em **Sim**.  

![Conexão RDP](/images/azure-vm-connect.png)  

---

## 🌐 Instalar servidor Web (IIS)
No **PowerShell** da VM, execute:  

```powershell
Install-WindowsFeature -name Web-Server -IncludeManagementTools
