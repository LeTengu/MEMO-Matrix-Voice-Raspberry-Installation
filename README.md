
# MEMO-Matrix-Voice-Raspberry-Installation

<br />
<h1>I    Installation Raspberry</h1>

1) Installer Raspbian et fichiers : « wpa_supplicant.conf » et « ssh » sur la carte SD.
2) Installer le Respeaker Matrix-Voice sur le Raspberry.
3) Insérer la carte SD dans le Rasberry.
4) Enclencher le câble d'alimentation sur le Raspberry.



<h1>II   Installation software (connexion raspberry en SSH)</h1>

<h3>a) configurer raspberry</h3>

     sudo raspi-config

1) changement hostname :      NETWORK OPTIONS >> Hostname      (pour moi: raspi-tengu).
2) utilisation de toute la carte. SD :    ADVANCED OPTIONS >> Expand Filesystem.
3) Localisation :    Options >> Change Timezone    (pour moi: Europe Paris)
4) Localisation :    Options >> Change Wi-fi Country    (pour moi: France)
5) Sauvegarder et rebooter

<h3>b) mise à jour:</h3>

1)     sudo apt-get update
2)     sudo apt-get upgrade
3)     sudo reboot

<h3>c) installation git :</h3>

     sudo apt-get install git

<h3>d) installation Matrix Voice :</h3>

1)     curl https://apt.matrix.one/doc/apt-key.gpg | sudo apt-key add - echo "deb https://apt.matrix.one/raspbian $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/matrixlabs.list
2)     sudo apt-get update
3)     sudo apt-get upgrade 
4)     sudo reboot
5)     sudo apt install matrixio-kernel-modules
6)     sudo reboot

<h3>e) installation snips depuis PC/MAC/autre avec SAM :</h3>

1.     sam connect raspi-tengu*
2.     sam init
3.     sam setup audio
4.    Taper "n" : ce n'est pas un kit !
5.    Vérifier que l'entrée Matrix-Voice est bien : Card 2.
6.    Vérifier que la sortie que l'on souhaite est : Card 0.
7.     sam test speaker
8.     sam test microphone

*raspi-tengu est le nom que vous avez donné à votre raspberry,<br />
peut-être remplacé par son adresse ip. 


<h3>f) modification fichier snips.toml via ssh :</h3>

     sudo nano /etc/snips.toml

chercher la ligne :<br />

     # mike =  "Built-in Microphone"

écrire en desous ou remplacer par :<br />

     mike = "MATRIXIO-SOUND: - (hw:2,0)"

puis rebooter.

<h3>g) retour sur le PC/MAC/autre pour installer l'assistant :</h3>

     sam install assistant
     
# Enjoy :-)
