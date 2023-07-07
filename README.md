# df-mod2-forensic-copy

#In this project I created a folder with forensic evidence and made a copy of that folder ensuring that the SHA256 values match for both folders. This means that the copy folder is a forensically sound copy. For evidence I just made some fake files along with some images that I had on my desktop already.


##Here are the hashes from the original evidence folder: 
File: cat.jpeg, SHA256 Hash: 4481CFA3CF72821BED87AB6BCB30F1784836E6B46FACF5E059A933E4DC1C0372
File: fake passwords.txt, SHA256 Hash: 767F5F745063EC5B1E5B70792BC576D3EDD4B2CACED8FC68C3C68534C8ED0F9E
File: fakeObituary.docx, SHA256 Hash: 8C53EADD7431E5B9E46D7A75BF503165E46392050EE52D0839D9C35367CF80F0
File: fakeSalary.xlsx, SHA256 Hash: E6996E08EF537A74AB4103C21967AD205E920CF8340D5AFB8B792752ADFC2795
File: garfield.jpeg, SHA256 Hash: A41A713BF4C7141BF7B85325926EAA3B8021F7AD1F7BEB290115B7AC3840A10E

##Here are the hashes from the copied evidence folder: 
File: cat.jpeg, SHA256 Hash: 4481CFA3CF72821BED87AB6BCB30F1784836E6B46FACF5E059A933E4DC1C0372
File: fake passwords.txt, SHA256 Hash: 767F5F745063EC5B1E5B70792BC576D3EDD4B2CACED8FC68C3C68534C8ED0F9E
File: fakeObituary.docx, SHA256 Hash: 8C53EADD7431E5B9E46D7A75BF503165E46392050EE52D0839D9C35367CF80F0
File: fakeSalary.xlsx, SHA256 Hash: E6996E08EF537A74AB4103C21967AD205E920CF8340D5AFB8B792752ADFC2795
File: garfield.jpeg, SHA256 Hash: A41A713BF4C7141BF7B85325926EAA3B8021F7AD1F7BEB290115B7AC3840A10E

###As you can see, the hashes from each folder match which means I did the project correctly.

####To get the hashes into a separate file and format them neatly I used this PowerShell script: 
Get-ChildItem | ForEach-Object {
    $file = $_
    $hash = Get-FileHash -Path $file.FullName -Algorithm SHA256
    $output = "File: {0}, SHA256 Hash: {1}" -f $file.Name, $hash.Hash
    $output | Out-File -FilePath "original hashes.txt" -Append
}
