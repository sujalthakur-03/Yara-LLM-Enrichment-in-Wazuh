# Yara-LLM-Enrichment-in-Wazuh
LLMs use deep learning to process and generate human language, enhancing efficiency across industries, including security. YARA detects malware by identifying patterns but needs human analysis. ChatGPT, an OpenAI LLM-powered chatbot, enriches YARA alerts with context, helping security teams better understand and assess threats.

# Ubuntu 22.04 Endpoint
## ➡ Step 1: Yara Installation
   ## - Install Dependencies
      
      apt-get install automake libtool make gcc pkg-config
      apt-get install flex bison
      apt install libjansson-dev
      apt install libmagic-dev
      
  ## - Install Yara
      
      wget https://github.com/VirusTotal/yara/archive/refs/tags/v4.5.1.tar.gz
      tar xzvf v4.5.1.tar.gz
      cd yara-4.5.1
      ./bootstrap.sh
      ./configure --enable-cuckoo --enable-magic --enable-dotnet
      make
      make install
      make check
      

## ➡ Step 2: Install Yara Rules
      cd /opt/yara-4.5.1/rules
      ./index_gen.sh

## ➡ Step 3: Now add the [yara.sh](https://github.com/sujalthakur-03/Yara-LLM-Enrichment-in-Wazuh/blob/main/yara.sh) in /var/ossec/active-response/bin

## ➡ Wazuh-Server Config
   - Paste the [Decoders](https://github.com/sujalthakur-03/Yara-LLM-Enrichment-in-Wazuh/blob/main/local_decoder.xml) in /var/ossec/etc/decoders/local_decoder.xml
   - Paste the [Rules](https://github.com/sujalthakur-03/Yara-LLM-Enrichment-in-Wazuh/blob/main/local_rules.xml) in /var/ossec/etc/rules/local_rules.xml
   - In [ossec.conf](https://github.com/sujalthakur-03/Yara-LLM-Enrichment-in-Wazuh/blob/main/ossec.conf) Add the following block
