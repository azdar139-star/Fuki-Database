def fetch_data(num):
    jbk_banner()
    print(f"\n{W}[{G}*{W}] {C}SEARCHING SECURE CLOUD...{RESET}")
    
    url = f"https://howler-database-api.vercel.app/api/lookup?phone={num}"
    
    # Adding headers to look like a real browser
    headers = {
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36'
    }
    
    try:
        # Increase timeout to 20 to allow for slow connections
        response = requests.get(url, headers=headers, timeout=20)
        
        # Check if the website actually loaded (Status 200)
        if response.status_code == 200:
            res = response.json()
            
            print(f"\n{C}┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓")
            print(f"{C}┃{W}            🔍 SEARCH RESULTS              {C}┃")
            print(f"{C}┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┩")
            
            if res:
                for key, val in res.items():
                    if "howler" in str(key).lower(): continue 
                    
                    if isinstance(val, list):
                        for item in val:
                            for k, v in item.items():
                                print(f"{C}┃ {G}{k.upper():<12} {W}: {W}{v:<25} {C}┃")
                            print(f"{C}┢━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┩")
                    else:
                        print(f"{C}┃ {G}{key.upper():<12} {W}: {W}{val:<25} {C}┃")
                print(f"{C}┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛")
            else:
                print(f"{C}┃ {R}          [!] NO DATA FOUND!              {C}┃")
                print(f"{C}┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛")
        else:
            print(f"{R}[!] SERVER REJECTED REQUEST (Code: {response.status_code})")
            
    except requests.exceptions.ConnectionError:
        print(f"{R}[!] CONNECTION FAILED! Check your internet or VPN.")
    except requests.exceptions.Timeout:
        print(f"{R}[!] SERVER TIMED OUT! The API is too slow.")
    except Exception as e:
        print(f"{R}[!] AN UNEXPECTED ERROR OCCURRED: {e}")
        
    input(f"\n{Y}Press Enter to return to Menu...{RESET}")
