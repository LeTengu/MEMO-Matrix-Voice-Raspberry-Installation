# MEMO-Matrix-Voice-Raspberry-Installation


I    Installation Raspberry

1) Installer Raspbian et fichiers : « wpa_supplicant.conf » et « ssh » sur la carte SD.
2) Installer le Respeaker Matrix-Voice sur le Raspberry.
3) Insérer la carte SD dans le Rasberry.
4) Enclencher le câble d'alimentation sur le Raspberry.



II   Installation software (connexion raspberry en SSH)

a) configurer raspberry

     sudo raspi-config

1) changement hostname :      NETWORK OPTIONS >> Hostname      (pour moi: raspi-tengu).
2) utilisation de toute la carte. SD :    ADvANCED OPTIONS >> Expand Filesystemde.
3) Localisation :    Options >> Change Timezone    (pour moi: Europe Paris)
4) Localisation :    Options >> Change Wi-fi Country    (pour moi: France)
5) Sauvegarder et rebooter

b) mise à jour:

1)     sudo apt-get update
2)     sudo apt-get upgrade
3)     sudo reboot

c) installation git :

     sudo apt-get install git

d) installation Matrix Voice :

1)     curl https://apt.matrix.one/doc/apt-key.gpg | sudo apt-key add - echo "deb https://apt.matrix.one/raspbian $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/matrixlabs.list
2)     sudo apt-get update
3)     sudo apt-get upgrade 
4)     sudo reboot
5)     sudo apt install matrixio-kernel-modules
6)     sudo reboot

e) installation snips depuis PC/MAC/autre avec SAM :

1.     sam connect raspi-tengu
2.     sam init
3.     sam setup audio
4.    Taper "n" : ce n'est pas un kit !
5.    Vérifier que l'entrée Matrix-Voice est bien : Card 2.
6.    Vérifier que la sortie que l'on souhaite est : Card 0.
7.     sam test speaker
8.     sam test microphone

f) modification fichier snips.toml via ssh :

     sudo nano /etc/snips.toml

chercher la ligne :
      # mike = ""

écrire en desous ou remplacer par :
      mike = "MATRIXIO-SOUND: - (hw:2,0)"

puis rebooter.

g) retour sur le PC/MAC/autre pour installer l'assistant :

     sam install assistant
     
# Enjoy :-)
