## Ön Hazırlık
- Proje ansible yüklü bir makine üzerine kopyalanır
  ```
  apt install ansible git sshpass
  cd /opt
  git clone https://github.com/aciklab/ansible-mico.git
  cd ansible-mico
  ```
- Mico'nun deb uzantılı paketleri /opt/ansible-mico/files/deb dizini altına atılır  
  ![deb](https://user-images.githubusercontent.com/11041014/159276912-f69bb0f4-a9bd-487f-a986-10f3a3c534b1.png)

- Mico'nun rpm uzantılı paketleri /opt/ansible-micofiles/rpm/ dizini altına atılır
  ![rpm](https://user-images.githubusercontent.com/11041014/159277171-27d1bd95-41b1-49ca-b375-bb1c936ce321.png)
  
- /opt/ansible-mico/inventory/hosts dosyası içerisine miço ajanı kurulacak makinelerin ip adresi, yetkili kullanıcısı gibi bilgiler eklenir.
  ```
  [Rpm]
  192.168.5.10 ansible_ssh_user=root ansible_ssh_pass=1


  [deb]
  192.168.5.11 ansible_ssh_user=test ansible_ssh_pass=1 ansible_sudo_pass=1
  ```
  RPM tabanlı makineler [rpm] başlığı altına örnekteki gibi eklenir.
  Debian tabanlı makineler [deb] başlığı altına örnekteki gibi eklenir.
- /opt/ansible-mico/vars/mico-vars.yml dosyası içerisine mico sunucusunun ip adresi yazılır
  ```
  mico_server: "192.168.5.4"
  ```
## Kullanım
- Debian tabanlı işletim sistemlerine dağıtım için aşağıdaki komut çalıştırılır
  ```
  cd /opt/ansible-mico/
  ansible-playbook /opt/ansible-mico/playbooks/deb.yml 
  ```
- RPM tabanlı işletim sistemlerine dağıtım için aşağıdaki komut çalıştırılır
  ```
  cd /opt/ansible-mico/
  ansible-playbook playbooks/rpm.yml
  ```
