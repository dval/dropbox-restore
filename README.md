dropbox-restore
===============

Restore any dropbox folder to a previous state. If a file did not exist at the specified time, it will be deleted.

Example
-------
To restore the folder "/photos/nyc" to the way it was on March 9th, 2013:

    python2.7 restore.py /photos/nyc 2013-03-09
    
Note that the path "/photos/nyc" should be relative to your Dropbox folder; it should not include the path to the Dropbox folder on your hard drive. You will be prompted to confirm access to your Dropbox account through your web browser.

Installation
------------
1. First make sure that Python 2.7 and pip are installed. 
2. Then install the Dropbox Python API with the following command.

    sudo pip install dropbox

3. Download restore.py from Github

Forking
-------
If you fork this project, you must obtain your own API keys from Dropbox and insert them into the APP\_KEY and APP\_SECRET fields.

Time
----
Specifying a time is not officially supported because the time zone is ignored currently. However, it seems like Dropbox always uses UTC, so you can try specifying UTC times at your own risk by specifying the date and time in the format YYYY-MM-DD-HH-MM-SS on the command line. Be warned that Dropbox's documentation does not guarantee that they will always use UTC, so this can break at any time.

-Donations
----------
-If you would like to make a donation, you can use the PayPal button on my website: http://cclark.me


#Trying to port this to Python3:
many errors and some architectual issues.

    192:Development dylan$ cd dropbox-restore
    192:dropbox-restore dylan$ ls
    LICENSE		README.md	restore.py

####Ran command, got the following error:

    Traceback (most recent call last):
      File "restore.py", line 113, in <module>
        main()
      File "restore.py", line 102, in main
        root_path = root_path_encoded.decode(sys.stdin.encoding)
    AttributeError: 'str' object has no attribute 'decode'

####Ran command, got the following error:

    Traceback (most recent call last):
      File "restore.py", line 113, in <module>
        main()
      File "restore.py", line 102, in main
        root_path = root_path_encoded.decode(sys.stdin.encoding)
    AttributeError: 'str' object has no attribute 'decode'

####Ran command, got the following (then an error):

1. Go to: https://www.dropbox.com/1/oauth2/authorize?response_type=code&client_id=xxxxxxxxxxxxx
2. Click "Allow" (you might have to log in first)
3. Copy the authorization code.

```
Traceback (most recent call last):
  File "restore.py", line 113, in <module>
    main()
  File "restore.py", line 108, in main
    client = login('token.dat')
  File "restore.py", line 41, in login
    access_token = authorize()
  File "restore.py", line 31, in authorize
    code = input("Enter the authorization code here: ").strip()
UnboundLocalError: local variable 'input' referenced before assignment
```

####Ran command, got the following (then an error):

1. Go to: https://www.dropbox.com/1/oauth2/authorize?client_id=xxxxxxxxxxxxx&response_type=code
2. Click "Allow" (you might have to log in first)
3. Copy the authorization code.

```
Traceback (most recent call last):
  File "restore.py", line 114, in <module>
    main()
  File "restore.py", line 109, in main
    client = login('token.dat')
  File "restore.py", line 42, in login
    access_token = authorize()
  File "restore.py", line 27, in authorize
    input = input
UnboundLocalError: local variable 'input' referenced before assignment
```

####Ran command, got the following error:

1. Go to: https://www.dropbox.com/1/oauth2/authorize?response_type=code&client_id=xxxxxxxxxxxxx
2. Click "Allow" (you might have to log in first)
3. Copy the authorization code.

```
Traceback (most recent call last):
  File "restore.py", line 113, in <module>
    main()
  File "restore.py", line 108, in main
    client = login('token.dat')
  File "restore.py", line 41, in login
    access_token = authorize()
  File "restore.py", line 31, in authorize
    code = raw_input("Enter the authorization code here: ").strip()
NameError: global name 'raw_input' is not defined
```

####Ran command, got the following error:

1. Go to: https://www.dropbox.com/1/oauth2/authorize?response_type=code&client_id=xxxxxxxxxxxxx
2. Click "Allow" (you might have to log in first)
3. Copy the authorization code.
Enter the authorization code here: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

```
Traceback (most recent call last):
  File "restore.py", line 113, in <module>
    main()
  File "restore.py", line 109, in main
    restore_folder(client, root_path, cutoff_datetime, verbose=True)
  File "restore.py", line 80, in restore_folder
    print('Restoring folder: ' + path.encode('utf8'))
TypeError: Can't convert 'bytes' object to str implicitly
```

####Ran command, got the following error:

    Traceback (most recent call last):
      File "restore.py", line 113, in <module>
        main()
      File "restore.py", line 109, in main
        restore_folder(client, root_path_encoded.decode(sys.stdin.encoding), cutoff_datetime, verbose=True)
    AttributeError: 'str' object has no attribute 'decode'


####Ran command, got the following error:

    Traceback (most recent call last):
      File "restore.py", line 114, in <module>
        main()
      File "restore.py", line 110, in main
        restore_folder(client, root_path, cutoff_datetime, verbose=True)
      File "restore.py", line 84, in restore_folder
        include_deleted=True)
      File "/Library/Frameworks/Python.framework/Versions/3.3/lib/python3.3/site-packages/dropbox-2.2.0-py3.3.egg/dropbox/client.py", line 874, in metadata
        path = "/metadata/%s%s" % (self.session.root, format_path(path))
      File "/Library/Frameworks/Python.framework/Versions/3.3/lib/python3.3/site-packages/dropbox-2.2.0-py3.3.egg/dropbox/client.py", line 36, in format_path
        path = re.sub(r'/+', '/', path)
      File "/Library/Frameworks/Python.framework/Versions/3.3/lib/python3.3/re.py", line 170, in sub
        return _compile(pattern, flags).sub(repl, string, count)
    TypeError: can't use a string pattern on a bytes-like object
    
    
    
