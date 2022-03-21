## Ön Hazırlık
- Proje ansible yüklü bir makine üzerine kopyalanır
  ```
  apt install ansible git sshpass
  cd /opt
  git clone https://github.com/aciklab/ansible-mico.git
  cd ansible-mico
  ```
- Mico'nun deb uzantılı paketleri /opt/ansible-mico/files/deb dizini altına atılır  
- Mico'nun rpm uzantılı paketleri /opt/ansible-micofiles/rpm/ dizini altına atılır
- inventory/hosts dosyası içerisine miço ajanı kurulacak makinelerin ip adresi, yetkili kullanıcısı gibi bilgiler eklenir.
  ```
  [Rpm]
  192.168.5.10 ansible_ssh_user=root ansible_ssh_pass=1


  [deb]
  192.168.5.11 ansible_ssh_user=test ansible_ssh_pass=1 ansible_sudo_pass=1
  ```
  RPM tabanlı makineler [rpm] başlığı altına örnekteki gibi eklenir.
  Debian tabanlı makineler [deb] başlığı altına örnekteki gibi eklenir.
- vars/mico-vars.yml dosyası içerisine mico sunucusunun ip adresi yazılır
  ```
  mico_server: "192.168.5.4"
  ```
## Kullanım
- Debian tabanlı işletim sistemlerine dağıtım için aşağıdaki komut çalıştırılır
  ```
  ansible-playbook playbooks/deb.yml 
  ```
- RPM tabanlı işletim sistemlerine dağıtım için aşağıdaki komut çalıştırılır
  ```
  ansible-playbook playbooks/rpm.yml
  ```