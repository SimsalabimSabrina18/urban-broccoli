import smtplib

import string





def unicodetoascii(text):



    uni2ascii = {

            ord('\xe2\x80\x99'.decode('utf-8')): ord("'"),

            ord('\xe2\x80\x9c'.decode('utf-8')): ord('"'),

            ord('\xe2\x80\x9d'.decode('utf-8')): ord('"'),

            ord('\xe2\x80\x9e'.decode('utf-8')): ord('"'),

            ord('\xe2\x80\x9f'.decode('utf-8')): ord('"'),

            ord('\xc3\xa9'.decode('utf-8')): ord('e'),

            ord('\xe2\x80\x9c'.decode('utf-8')): ord('"'),

            ord('\xe2\x80\x93'.decode('utf-8')): ord('-'),

            ord('\xe2\x80\x92'.decode('utf-8')): ord('-'),

            ord('\xe2\x80\x94'.decode('utf-8')): ord('-'),

            ord('\xe2\x80\x94'.decode('utf-8')): ord('-'),

            ord('\xe2\x80\x98'.decode('utf-8')): ord("'"),

            ord('\xe2\x80\x9b'.decode('utf-8')): ord("'"),



            ord('\xe2\x80\x90'.decode('utf-8')): ord('-'),

            ord('\xe2\x80\x91'.decode('utf-8')): ord('-'),



            ord('\xe2\x80\xb2'.decode('utf-8')): ord("'"),

            ord('\xe2\x80\xb3'.decode('utf-8')): ord("'"),

            ord('\xe2\x80\xb4'.decode('utf-8')): ord("'"),

            ord('\xe2\x80\xb5'.decode('utf-8')): ord("'"),

            ord('\xe2\x80\xb6'.decode('utf-8')): ord("'"),

            ord('\xe2\x80\xb7'.decode('utf-8')): ord("'"),



            ord('\xe2\x81\xba'.decode('utf-8')): ord("+"),

            ord('\xe2\x81\xbb'.decode('utf-8')): ord("-"),

            ord('\xe2\x81\xbc'.decode('utf-8')): ord("="),

            ord('\xe2\x81\xbd'.decode('utf-8')): ord("("),

            ord('\xe2\x81\xbe'.decode('utf-8')): ord(")"),





                            }

    return text.decode('utf-8').translate(uni2ascii).encode('ascii')









myfile = open ("data.txt", "r")

predata = str(myfile.readlines())

data = unicodetoascii(predata.translate(None, string.punctuation))

stringValue = data.replace("xe2x80x9c","").replace("xe2x80x9d","").replace("xe2x80x93","")

array = stringValue.split()

array.reverse()

print(array)









# From & To, Message



fromaddr = 'enter your address here'

toaddrs = 'enter recipient address here'



msg = 'Subject: %s\n\n%s' % ('enter subject here','enter main message here')



# Credentials



username = 'enter your address here'

password = 'enter your email password here'





server = smtplib.SMTP('smtp.gmail.com:587')

server.starttls()

server.login(username,password)







for x in range(len(array)):



	msg = array[x]



	server.sendmail(fromaddr,toaddrs,msg)

	print(x)





server.quit()


