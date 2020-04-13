# KVM

[source](https://rousseau-alexandre.fr/tutorial/2018/10/02/kvm.html)


**Créer une image**

        qemu-img create kali.img 10G


**Créer et lancer une VM**

Ici on indique le nom de l'image disque créé juste avant, met 1G de ram et surtout on met place notre iso dans un lecteur de disque.
A noter que l'on indique bien de booter sur le disque ! (Si on omet cet argument le disque dur sera choisi par défaut)

        qemu-kvm -hda kali.img -boot d -cdrom kali-linux-xfce-2018.3a-amd64.iso -m 1G

Une fois la bête installée on la démarre tout simplement :

        qemu-kvm -hda kali.img -m 1G

A noter que le copier/coller ne fonctionne pas en l'état, (il faut pour cela passer pat spice et virt-manager ?).
Par contre on peut, et c'est même plus simple ainsi, se connecter en serial ou en ssh à l'intérieur de notre guest.
Ainsi on utilise notre terminal et tous les avantages que ça implique. [source](https://wiki.qemu.org/Documentation/Networking#How_to_get_SSH_access_to_a_guest)
Pour se faire :

        qemu-kvm -hda kali.img -m 1G -device e1000,netdev=net0 -netdev user,id=net0,hostfwd=tcp::5555-:22

Et on se connecte depuis notre hôte en ssh avec :

         ssh localhost -p 5555

Une fois la possibilité de se connecter sur la becane il est peut-etre plus très utile de lancer l'interface graphique.


On peut aussi utiliser virsh, virt-install (et autre ?) pour créé une machine virtuel, bien qu'ici on bien plus d'options:

        virt-install  –name=itzgeekguest  –ram=1024  –vcpus=1  –cdrom=/tmp/CentOS-6.5-x86_64-minimal.iso –os-type=linux         \
            –os-variant=rhel6  –network bridge=virbr0 –graphics=spice                                                              \
            –disk path=/var/lib/libvirt/images/itzgeekguest.dsk,size=4virt-install                                              \
            –name=itzgeekguest  –ram=1024  –vcpus=1  –cdrom=/tmp/CentOS-6.5-x86_64-minimal.iso –os-type=linux –os-variant=rhel6 \
            –network bridge=br0 –graphics=spice  –disk path=/var/lib/libvirt/images/itzgeekguest.dsk,size=4


**Convertir une image vmdk vers qcow2**

`qemu-img convert -f vmdk -O qcow2 image.vmdk image.qcow2`


**Ajouter le support du copier/coller avec Spice**

Sur le guest:

`apt install spice-vdagent`


