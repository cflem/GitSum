### GitSum

GitSum is more of a project I designed in order to learn the basics of RSA
encryption, but if you're interested feel free to take a look.

GitSum is a userscript, which means its installed in the user's browser and
run on a specific set of pages, which in this case is all. The script looks
for specially designed <pre> tags that contain an encrypted checksum of a
file, theoretically the file to be downloaded. It uses the signer's SSH keys,
which are stored on GitHub under their identity, to decrypt the signature
and compare it with the real checksum of the file. It adds a tag next to the
signature declaring it either valid or invalid.

A signature is created as such:
1. Take the SHA-1 checksum of the file.
2. Use OpenSSL or some other such tool to "sign" the checksum with your
   private key (must be one that you have stored on GitHub.)
Simple as that!

How to embed signatures in HTML code:
> <pre data-relation="signature" data-signer="Your Username" data-file="the URL of the file you're signing">PASTE SIGNATURE HERE</pre>
