# Simple ACPI parser for i3blocks

This is a simple parser of the `acpi -b` output for laptops with more than one
battery. It displays one icon per battery, depending on whether it is charging,
and how time is remaining.

Because remaining time is calculated based on the discharge rate, ACPI can not
provide us with the total remaining time for all batteries. Thus, the "time
remaining" is only true for the currently discharging battery, and the new
estimate will only be provided once the system switches over to the next
battery, and so forth.

The output is created for my i3blocks configuration (which uses fontawesome,
IIRC).

## Usage

Create a virtualenv:

```sh
mkdir ~/.vens
virtualenv ~/.venvs/battery-status
source ~/.venvs/battery-status-bin/activate
```

Install the dependencies:

```sh
pip install -r requirements.txt
```

Copy the shell script somewhere in your `$PATH`:

```sh
cp battery.sh ~/bin
```

Add the entry to your `i3blocks.conf`:

```conf
[battery]
command=~/bin/battery.sh
interval=30
markup=pango
```

The shell script automatically loads the virtualenv and then runs the script.
