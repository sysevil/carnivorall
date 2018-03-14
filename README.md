 
 ================================================================================================
                                                                                     
 ▄████▄   ▄▄▄       ██▀███   ███▄    █  ██▓ ██▒   █▓ ▒█████   ██▀███   ▄▄▄       ██▓     ██▓    
▒██▀ ▀█  ▒████▄    ▓██ ▒ ██▒ ██ ▀█   █ ▓██▒▓██░   █▒▒██▒  ██▒▓██ ▒ ██▒▒████▄    ▓██▒    ▓██▒    
▒▓█    ▄ ▒██  ▀█▄  ▓██ ░▄█ ▒▓██  ▀█ ██▒▒██▒ ▓██  █▒░▒██░  ██▒▓██ ░▄█ ▒▒██  ▀█▄  ▒██░    ▒██░    
▒▓▓▄ ▄██▒░██▄▄▄▄██ ▒██▀▀█▄  ▓██▒  ▐▌██▒░██░  ▒██ █░░▒██   ██░▒██▀▀█▄  ░██▄▄▄▄██ ▒██░    ▒██░    
▒ ▓███▀ ░ ▓█   ▓██▒░██▓ ▒██▒▒██░   ▓██░░██░   ▒▀█░  ░ ████▓▒░░██▓ ▒██▒ ▓█   ▓██▒░██████▒░██████▒
░ ░▒ ▒  ░ ▒▒   ▓▒█░░ ▒▓ ░▒▓░░ ▒░   ▒ ▒ ░▓     ░ ▐░  ░ ▒░▒░▒░ ░ ▒▓ ░▒▓░ ▒▒   ▓▒█░░ ▒░▓  ░░ ▒░▓  ░
  ░  ▒     ▒   ▒▒ ░  ░▒ ░ ▒░░ ░░   ░ ▒░ ▒ ░   ░ ░░    ░ ▒ ▒░   ░▒ ░ ▒░  ▒   ▒▒ ░░ ░ ▒  ░░ ░ ▒  ░
░          ░   ▒     ░░   ░    ░   ░ ░  ▒ ░     ░░  ░ ░ ░ ▒    ░░   ░   ░   ▒     ░ ░     ░ ░   
░ ░            ░  ░   ░              ░  ░        ░      ░ ░     ░           ░  ░    ░  ░    ░  ░
░                                               ░                                               
                                               
 ================================================================================================ 
                --=={ Looking for sensitive information on local network }==-- 
                
                
# Authors: L0stControl and BFlag

# Intro

Scan internal network looking for files with sensitive information on SMB shares. 

# Usage

    Usage: ./carnivoral.sh [options]
    
      -n, --network <CIDR>                        192.168.0.0/24
      -l, --list <inputfilename>                  List of hosts/networks
      -d, --domain <domain>                       Domain network
      -u, --username <guest>                      Domain username 
      -p, --password <guest>                      Domain password
      -o, --only <contents|filenames|yara|regex>  ONLY by contents, filenames, yara rules or regex
      -m, --match "user passw senha"              Strings to match inside files (not default)
      -r, --regex "4[0-9]{12}[0-9]?{3}"           Search contents using REGEX
      -y, --yara <juicy_files.txt>                Enable Yara search patterns (not default)
      -e, --emails <y|n>                          Download all \"*.pst\" files (Prompt by default) 
      -D, --delay <Number>                        Delay between requests  
      -h, --help                                  Display options
        
    Ex1: ./carnivorall.sh -n 192.168.0.0/24 -u Admin -p Admin -d COMPANY  
    Ex2: ./carnivorall.sh -n 192.168.0.0/24 -u Admin -p Admin -d COMPANY -o filenames
    Ex3: ./carnivorall.sh -n 192.168.0.0/24 -u Admin -p Admin -d COMPANY -o yara -y juicy_files.txt


# Requirements:

- smbclient 
- GhostScript
- zip
- ruby
- yara (only to use -y option)
