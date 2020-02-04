# yara-sandbox


local scan
~~~~
cd /tmp
sudo apt-get install -y clamav
git clone https://github.com/Hestat/lw-yara.git
sudo clamscan -ir -d /tmp/lw-yara/ /tmp/*

 --infected            -i             Only print infected files
 --recursive[=yes/no(*)]  -r          Scan subdirectories recursively
 --database=FILE/DIR   -d FILE/DIR    Load virus database from FILE or load all supported db files from DIR

$ sudo clamscan -ir -l /tmp/scanresults.txt -d /tmp/lw-yara/lw-rules_index.yar -d /tmp/lw-yara/lw.hdb /home

----------- SCAN SUMMARY -----------
Known viruses: 997
Engine version: 0.102.1
Scanned directories: 53
Scanned files: 540
Infected files: 0
Data scanned: 70.83 MB
Data read: 30.12 MB (ratio 2.35:1)
Time: 49.930 sec (0 m 49 s)
vagrant@lampstack-01:/tmp$ sudo cat /tmp/scanresults.txt

-------------------------------------------------------------------------------


----------- SCAN SUMMARY -----------
Known viruses: 997
Engine version: 0.102.1
Scanned directories: 53
Scanned files: 540
Infected files: 0
Data scanned: 70.83 MB
Data read: 30.12 MB (ratio 2.35:1)
Time: 49.930 sec (0 m 49 s)



vagrant@lampstack-01:/tmp$ sudo clamscan -ir -d /tmp/lw-yara/ /tmp/*
/tmp/lw-yara/includes/magento_sucuri_001.yar: YARA.magento_sucuri_malware.UNOFFICIAL FOUND
/tmp/lw-yara/includes/amadey-botnet012919.yar: YARA.infected_01_29_19_amadey_botnet_f_st_style.UNOFFICIAL FOUND
/tmp/lw-yara/includes/magecart1.yar: YARA.magecart.UNOFFICIAL FOUND
/tmp/lw-yara/includes/wp-thumb-081418.yar: YARA.wp_timthumb_081418.UNOFFICIAL FOUND
/tmp/lw-yara/includes/scanner_obfuscated_shell.yar: YARA.infected_05_29_18_case109_case109_scanner.UNOFFICIAL FOUND
/tmp/lw-yara/includes/s3sshll-093018.yar: YARA.infected_09_30_18_s3sshll.UNOFFICIAL FOUND
/tmp/lw-yara/includes/usaa-phishing001.yar: YARA.phishing_actor_emails.UNOFFICIAL FOUND
/tmp/lw-yara/includes/license-091918.yar: YARA.infected_09_19_18_shell1_LICENSE.UNOFFICIAL FOUND
/tmp/lw-yara/includes/multi-miner-exe.yar: YARA.miner_g_p_0.UNOFFICIAL FOUND
/tmp/lw-yara/includes/wp-shells_case137.yar: YARA.wp_layouts.UNOFFICIAL FOUND
/tmp/lw-yara/includes/phishing-actors.yar: YARA.phishing_actor_emails.UNOFFICIAL FOUND
/tmp/lw-yara/includes/wordpress_admin_bd_082218.yar: YARA.infected_language_ru_082218.UNOFFICIAL FOUND
/tmp/lw-yara/includes/miner.yar: YARA.crypto_miner.UNOFFICIAL FOUND
/tmp/lw-yara/includes/drupal_injection_134.yar: YARA.drupal_injection_case134.UNOFFICIAL FOUND
/tmp/lw-yara/includes/052618-drupalsite.yar: YARA._infected_05_26_18_tekel.UNOFFICIAL FOUND
/tmp/lw-yara/includes/wordpress-injection-2.yar: YARA.wordpress2_ico_injection_detected.UNOFFICIAL FOUND
/tmp/lw-yara/includes/mailer1.yar: YARA.php_mailer_1.UNOFFICIAL FOUND
/tmp/lw-yara/includes/alfa-shell.yar: YARA.alfa_webshell.UNOFFICIAL FOUND
/tmp/lw-yara/includes/sucuri-wpcache.yar: YARA.infected_11_10_18_wp_cache.UNOFFICIAL FOUND
/tmp/lw-yara/includes/navytitanium.yar: YARA.uploader_wp_themes.UNOFFICIAL FOUND
/tmp/lw-yara/includes/drupal-index-ico-injection.yar: YARA.ico_injection_detected.UNOFFICIAL FOUND
/tmp/lw-yara/includes/annizod-xmr-miner.yar: YARA._case110_annizod_XMR_MINER.UNOFFICIAL FOUND
/tmp/lw-yara/includes/magecart5.yar: YARA.magecart_5.UNOFFICIAL FOUND
/tmp/lw-yara/includes/mass_bot_exploite_master.yar: YARA._07_14_18_mass_bot_exploite_master_drupal.UNOFFICIAL FOUND
/tmp/lw-yara/includes/php-gen-1.yar: YARA.generic_php_injection_1.UNOFFICIAL FOUND
/tmp/lw-yara/includes/magecart4.yar: YARA.magecart_4.UNOFFICIAL FOUND
/tmp/lw-yara/includes/chase-bank-phish2-082718.yar: YARA.phishing_actor_emails.UNOFFICIAL FOUND
/tmp/lw-yara/includes/4700up-jpg.yar: YARA.sig_4700up_jpg_jpg.UNOFFICIAL FOUND
/tmp/lw-yara/includes/miner-config.yar: YARA.crypto_miner_config_file_0.UNOFFICIAL FOUND
/tmp/lw-yara/includes/wordpress-bot-070419.yar: YARA.wordpress_bot1.UNOFFICIAL FOUND
/tmp/lw-yara/includes/media-shell.yar: YARA.media_shell.UNOFFICIAL FOUND
/tmp/lw-yara/includes/maersk-phishing-121318.yar: YARA.phishing_actor_emails.UNOFFICIAL FOUND
/tmp/lw-yara/includes/tekel.yar: YARA._infected_05_26_18_tekel.UNOFFICIAL FOUND
/tmp/lw-yara/includes/adobe-phishing001.yar: YARA.phishing_actor_emails.UNOFFICIAL FOUND
/tmp/lw-yara/includes/stats5-090618.yar: YARA.infected_09_06_18_shell4_stats5.UNOFFICIAL FOUND
/tmp/lw-yara/includes/indo-exploit.yar: YARA.indo_exploit_tool.UNOFFICIAL FOUND
/tmp/lw-yara/includes/uploader-shell2-093018.yar: YARA.infected_09_30_18_shell_ups.UNOFFICIAL FOUND
/tmp/lw-yara/includes/well-phishing0001.yar: YARA.phishing_well_fargo.UNOFFICIAL FOUND
/tmp/lw-yara/includes/uploader-shells-093018.yar: YARA.infected_09_30_18_shell_b.UNOFFICIAL FOUND
/tmp/lw-yara/includes/magecart2.yar: YARA.magecart_2.UNOFFICIAL FOUND
/tmp/lw-yara/includes/php-gen-0.yar: YARA.generic_php_injection_0.UNOFFICIAL FOUND
/tmp/lw-yara/includes/smartsheet091018.yar: YARA.infected_09_10_18_phishing_smartsheet_htaccess.UNOFFICIAL FOUND
/tmp/lw-yara/includes/magecart-sotheby.yar: YARA.magecart_sotheby.UNOFFICIAL FOUND
/tmp/lw-yara/includes/case117.yar: YARA.infected_09_25_18_webr00tv3.UNOFFICIAL FOUND
/tmp/lw-yara/includes/main_js_malvertising_139.yar: YARA.case139_main_js_malvertising.UNOFFICIAL FOUND
/tmp/lw-yara/includes/perl-socks-proxy.yar: YARA.perl_socks_proxy.UNOFFICIAL FOUND
/tmp/lw-yara/includes/sig_7409295928_WSO_gen.yar: YARA.sig_7409295928_WSO_generic.UNOFFICIAL FOUND
/tmp/lw-yara/includes/master134.yar: YARA.Master134_Malvertising.UNOFFICIAL FOUND
/tmp/lw-yara/includes/052918_case109.yar: YARA.infected_05_29_18_case109_case109_scanner.UNOFFICIAL FOUND
/tmp/lw-yara/includes/vul_jquery_fileupload_cve_2018_9206.yar: YARA.VUL_JQuery_FileUpload_CVE_2018_9206.UNOFFICIAL FOUND
/tmp/lw-yara/includes/cryptojacking_signatures.yar: YARA.crypto_jacking_signatures.UNOFFICIAL FOUND
/tmp/lw-yara/includes/drupalgeddon-0.yar: YARA.drupal_CVE_2018_7600_RCE_0.UNOFFICIAL FOUND
/tmp/lw-yara/includes/joomla-shell-case21.yar: YARA.infected_case21_temp.UNOFFICIAL FOUND
/tmp/lw-yara/includes/linkedin-phish001.yar: YARA.phishing_actor_emails.UNOFFICIAL FOUND
/tmp/lw-yara/includes/drupal_138.yar: YARA.case138_ps.UNOFFICIAL FOUND
/tmp/lw-yara/includes/eitest1.yar: YARA.eitest_injection_0.UNOFFICIAL FOUND
/tmp/lw-yara/includes/entabeam-phish.yar: YARA.phishing_actor_emails.UNOFFICIAL FOUND
/tmp/lw-yara/includes/crypto-jacking-1.yar: YARA.bad_packets_crypto_jacking_1.UNOFFICIAL FOUND
/tmp/lw-yara/includes/magecart3.yar: YARA.magecart_3.UNOFFICIAL FOUND
/tmp/lw-yara/includes/crypto-jacking-0.yar: YARA.bad_packets_crypto_jacking_0.UNOFFICIAL FOUND
/tmp/lw-yara/includes/x3d-phishing.yar: YARA.phishing_actor_emails.UNOFFICIAL FOUND
/tmp/lw-yara/includes/data_chaos_backdoor.yar: YARA.data_chaos_backdoor_shell.UNOFFICIAL FOUND
/tmp/lw-yara/includes/drupal_injection_001.yar: YARA.drupal_injection_06_09_18_case128_index.UNOFFICIAL FOUND
/tmp/lw-yara/includes/FOPO.yar: YARA.FOPOobfuscator.UNOFFICIAL FOUND
/tmp/lw-yara/includes/emotet-dropper.yar: YARA.emotet_dropper1.UNOFFICIAL FOUND
/tmp/lw-yara/includes/tbl-status-shell.yar: YARA.tbl_status_webshell.UNOFFICIAL FOUND
/tmp/lw-yara/includes/symlink-tool.yar: YARA.symlink_hacking_tool.UNOFFICIAL FOUND
/tmp/lw-yara/includes/xaishell.yar: YARA.phishing_actor_emails.UNOFFICIAL FOUND
/tmp/lw-yara/includes/case25-miners.yar: YARA.case25_miners_shared.UNOFFICIAL FOUND
/tmp/lw-yara/includes/acme092018.yar: YARA.infected_09_20_18_challenge_acme.UNOFFICIAL FOUND
/tmp/lw-yara/includes/BabaYaga.yar: YARA.WFYARAGEN_G4361_rules_1.UNOFFICIAL FOUND
/tmp/lw-yara/includes/cpanel-brute.yar: YARA.cpanel_brute_force_tool_brutus.UNOFFICIAL FOUND
/tmp/lw-yara/includes/total-donations-plugin.yar: YARA.the_ajax_caller.UNOFFICIAL FOUND
/tmp/lw-yara/includes/tryag-cpanel.yar: YARA.infected_01_13_19_cpanel_shell.UNOFFICIAL FOUND
/tmp/lw-yara/includes/me0w-js-miner.yar: YARA.meow_js_miner.UNOFFICIAL FOUND
/tmp/lw-yara/includes/rfi-perl-bot.yar: YARA.rfi_perl_bot.UNOFFICIAL FOUND
/tmp/lw-yara/includes/tndtttttttt.yar: YARA.infected_07_13_18_savoie_index.UNOFFICIAL FOUND
/tmp/lw-yara/includes/cache-mailer.yar: YARA.cache_mailer.UNOFFICIAL FOUND
/tmp/lw-yara/includes/hotopponents-sites.yar: YARA.infected_10_29_18_backdoors_script1.UNOFFICIAL FOUND
/tmp/lw-yara/includes/dark-shell.yar: YARA.dark_shell.UNOFFICIAL FOUND
/tmp/lw-yara/includes/js-malvertising.yar: YARA._06_04_18_case119_js_malvertising.UNOFFICIAL FOUND
/tmp/lw-yara/includes/luk_miner.yar: YARA.infected_06_03_18_case120_luk_ocl.UNOFFICIAL FOUND
/tmp/lw-yara/includes/drupal-CPREA57Webshell.yar: YARA.CPREA57_Webshell.UNOFFICIAL FOUND
/tmp/lw-yara/includes/mirai-routerscripts102018.yar: YARA.infected_10_20_18_scripts_dlink.UNOFFICIAL FOUND
/tmp/lw-yara/includes/saskmade-net-redirects.yar: YARA.infected_10_29_18_saskmade_net.UNOFFICIAL FOUND
/tmp/lw-yara/includes/fun-082618.yar: YARA.infected_08_26_18_shell_fun.UNOFFICIAL FOUND
/tmp/lw-yara/includes/upload-shell-082418.yar: YARA.infected_08_24_18_upload_shell_ubh.UNOFFICIAL FOUND
/tmp/lw-yara/includes/Tryag-File-Manager-1.yar: YARA.RUSSIAN_MAILER2018.UNOFFICIAL FOUND
/tmp/lw-yara/includes/prowli.yar: YARA._infected_06_07_18_prowli_botnet_IOC3_C2.UNOFFICIAL FOUND
/tmp/lw-yara/includes/sans-xme-072818.yar: YARA.jquery_prettyphoto.UNOFFICIAL FOUND
/tmp/lw-yara/includes/eitest_injection_1.yar: YARA.eitest_injection_1.UNOFFICIAL FOUND
/tmp/lw-yara/includes/paypal_phishing_kit_001.yar: YARA.phishing_actor_emails.UNOFFICIAL FOUND
/tmp/lw-yara/includes/620adjs_101118.yar: YARA.infected_10_11_18_620ad_js.UNOFFICIAL FOUND
/tmp/lw-yara/includes/injection-082218.yar: YARA.infected_082218_class_wp_widget_rss.UNOFFICIAL FOUND
/tmp/lw-yara/includes/PHP-Mailer-K.yar: YARA.PHP_Mailer_K.UNOFFICIAL FOUND
/tmp/lw-yara/includes/alfa-shells090618.yar: YARA.infected_09_06_18_internal_tool.UNOFFICIAL FOUND
/tmp/lw-yara/includes/case25-shells.yar: YARA.infected_case25_shells_1119.UNOFFICIAL FOUND
/tmp/lw-yara/includes/fack.yar: YARA.infected_188_120_231_151_2018_01_07a_shells_fack.UNOFFICIAL FOUND
/tmp/lw-yara/includes/microsoft-phish001.yar: YARA.phishing_actor_emails.UNOFFICIAL FOUND
/tmp/lw-yara/includes/day_uploader_shell.yar: YARA.sig_day_uploader_shell.UNOFFICIAL FOUND
/tmp/lw-yara/includes/alfa-perl.yar: YARA.alfa_perl_shell.UNOFFICIAL FOUND
/tmp/lw-yara/includes/CPR4616Webshell.yar: YARA.CPR4616_Webshell.UNOFFICIAL FOUND
/tmp/lw-yara/includes/symlink-bypass-082418.yar: YARA.infected_08_24_18_shell5_symlink_bypass.UNOFFICIAL FOUND
/tmp/lw-yara/includes/uploader-092718.yar: YARA.infected_09_27_18_uploader.UNOFFICIAL FOUND
/tmp/lw-yara/includes/navytitanium-122219.yar: YARA.backdoor_o9g.UNOFFICIAL FOUND

----------- SCAN SUMMARY -----------
Known viruses: 1000
Engine version: 0.102.1
Scanned directories: 23
Scanned files: 205
Infected files: 105
Data scanned: 21.33 MB
Data read: 8.36 MB (ratio 2.55:1)
Time: 116.973 sec (1 m 56 s)

~~~~

~~~~
>vagrant provision control02
==> control02: Running provisioner: ansible_local...
    control02: Installing Ansible...
The requested Ansible version (2.8.2) was not found on the guest.
Please check the Ansible installation on your Vagrant guest system (currently: 2.9.2),
or adapt the provisioner `version` option in your Vagrantfile.
See https://docs.vagrantup.com/v2/provisioning/ansible_common.html#version
for more information.
~~~~

~~~~
https://github.com/Hestat/lw-yara
https://github.com/Hestat/blazescan
~~~~
