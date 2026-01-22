# calculator
import tkinter as tk   # tkinter r short form tk
def on_click(key):  # _ ata single code ba function bujai key sob click handle kore 
 
    try:  
        current = screen_text.get()
        if key == "=":                #try dea code ru  korte bole crash khaile except r line ta dibe 
                                         #eval math pasapasi rake
            result = str(eval(current))
            screen_text.set(result)
        elif key == "C":
            screen_text.set("")        # if bar bar likle elif ar % 100 dea vug
        elif key == "%":               
            value = eval(current)
            result = str(value/100)
            screen_text.set(result)
        else :
             screen_text.set(current + key)  #lekhar baire kisu likle error asbe
    except:  screen_text.set("Error!")   

root = tk.Tk()            #window create kore sob er moddhe thakbe
root.title("Calculator")  # boxr upr Calculator leka asbe pore size kto
root.geometry("320x400")
 
screen_text = tk.StringVar() 
entry  = tk.Entry(root, textvariable = screen_text,font=("Arial", 26), bd = '10',insertwidth=4, width=12)
entry.grid (row = 0, column = 0,columnspan = 4, sticky = 'nsew' )
                                #textvariable=screen_text  variabler sathe box connect kore ja lekhi ta box ase                                
                                # columnspan coloum r alada alada na likhe akbare kaj kore shortcut
                                # bd r jaigai bg lekte pari then akta color dilm
                                #sticky= nsew ata box baki space vorat kore

buttons = [
    ['.','(',')','%'],
    ['7','8','9','/'],       # cal r face e ki ki rakbo 
    ['4','5','6','*'],
    ['1','2','3','-'], 
    ['C','0','=','+'],
 ]

for row_idx , row_val in enumerate(buttons , 1):  #kon button koi ase ata khuje je word likhi 
    root.rowconfigure(row_idx, weight = 1)        #resize kore screen boro sto korle
    for col_idx , char in enumerate( row_val ):   #col_idx ata loop kore 
     root.columnconfigure(col_idx, weight = 1)

     btn_color = 'white'
     if char =='C': btn_color = 'orange'   # btn color line 
     elif char =='=': btn_color = 'green'  # alada color chaile color code ase ota likle 
     
     tk.Button(root, text=char,font=("Arial", 16), bg = btn_color,
               command=lambda x =char: on_click(x)).grid(row=row_idx,column=col_idx, sticky='nsew')
                                        # ai line lekha dhore rake jate onno kisu likle seta jno thake
                                       #lambda sara  bujbe na kon function e number jabe ar x num sign freeze kore rake
                                       # grid row colm sob thik rakhe
root.mainloop()
       
