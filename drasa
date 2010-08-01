#!/bin/bash

echo -e "\033[4;2mWelcome to the italian spaghetti tax calculator by Nadalin Alessandro (http://www.odino.org)\033[0m"
echo -e "\033[4;2mprovided with no warranty and licensed under X11 ( former known as MIT ) license (see: http://en.wikipedia.org/wiki/MIT_License).\033[0m"

echo -e "\033[33m\nPlease enter your total incomings (excluded VAT):\033[0m"

read total
USED_INPS=2800
let ADDITIONAL_INPS=($total - 14000)*2/10
let INPS=$USED_INPS+ADDITIONAL_INPS
let IRAP=($total - 8000)*4/100

IRPEF_23=3450
IRPEF_27=3510
IRPEF_38=10260
IRPEF_41=8200

if [ $total -gt 15000 ]; then
  IRPEF=3450
  if [ $total -gt 28000 ]; then
    let IRPEF=$IRPEF+3510
    if [ $total -gt 55000 ]; then
      let IRPEF=$IRPEF+10260
      if [ $total -gt 75000 ]; then
        let IRPEF=$IRPEF+8200
      else
        let IRPEF=($total - 55000)*41/100+$IRPEF
      fi          
    else
      let IRPEF=($total - 28000)*38/100+$IRPEF
    fi    
  else
    let IRPEF=($total - 15000)*27/100+$IRPEF
  fi
else
  let IRPEF=($total)*23/100
fi

let ANNUAL=$total-$IRAP-$INPS-$IRPEF
let MONTHLY=$ANNUAL/12
let VAT=$total*2/10

echo -e ".....  +" "\033[4;32m$total\033[0m" "\ttotal earning"
echo -e ".....  ~" "\033[4;33m$VAT\033[0m" "\tvat"
echo -e ".....  -" "\033[4;31m$INPS\033[0m" "\tINPS"
echo -e ".....  -" "\033[4;31m$IRAP\033[0m" "\tIRAP"
echo -e ".....  -" "\033[4;31m$IRPEF\033[0m" "\tIRPEF"

echo -e "\033[32m\nYou earn\033[0m" "\033[1;32m$ANNUAL\033[0m" "\033[32mannually\033[0m"
echo -e "\033[32mYou earn\033[0m" "\033[1;32m$MONTHLY\033[0m" "\033[32mmonthly (12m)\033[0m"
