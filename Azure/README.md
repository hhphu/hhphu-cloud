# Azure CLI Cheat Sheet

## **`az GROUP SUBGROUP ACTION OPTIONAL_PARAMETERS`**
-----

- Retrieve information about the currently logged-in user

```bash
az ad signed-in-user show
```
![image](https://github.com/user-attachments/assets/5674cd07-4e61-4bec-825a-dc2cd11f3e5a)

- Retrieve  all users in the selected tenant

```bash
az ad user list
```

- Retrieve users starting with `wvusr-`

```bash
az ad user list --filter "startsWith('wvusr-', displayName)"
```

![image](https://github.com/user-attachments/assets/19f834d2-ea62-4ba5-a32c-5a79ed382869)

- List all the groups within a tenant

```bash
az ad group list
```

![image](https://github.com/user-attachments/assets/af3d167b-13ae-4bef-bf4d-317dc96f0941)

- List all the members of a group

```bash
az ad group member list --group $GROUP_NAME
```

![image](https://github.com/user-attachments/assets/39f3d285-9d6c-4ee2-99b1-abb32a9408a9)

- Clear a curret Azure CLI accoutn session and logging in with the new account

```bash
az account clear
az login -u $EMAIL -p $PASSWORD
```

![image](https://github.com/user-attachments/assets/fdd94d18-238e-4b13-8ffd-d8d057fc212e)

- Check all the roles assigned to a group

```bash
az role assignment list --assignee $GROUP_ID --all
```

![image](https://github.com/user-attachments/assets/7fc2011b-7c50-42d6-ac85-d5068a06d24b)

- List accessible key vaults

```bash
az keyvault list
```

![image](https://github.com/user-attachments/assets/2247df59-1cee-4854-bbae-a0185961c0b2)


- List accessible key vaults
  
  ```bash
az keyvault secret list --vault-name $VAULT_NAME
```

![image](https://github.com/user-attachments/assets/0084a1a0-03c2-4eca-a0b6-5e5a2186eb45)

- Reading the content of the secrets in the keyvault
```bash
az keyvault secret show --vault-name $VAULT_NAME --name $SECRET_NAME
```

![image](https://github.com/user-attachments/assets/3c39f0e1-28e1-484f-9157-bf325e9d38e5)



