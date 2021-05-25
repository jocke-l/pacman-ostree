pacman-ostree
=============

PoC for atomic upgrades in Arch Linux by using OSTree.

# Specification

The main goals of this PoC are to implement an upgrade mechanism that is:

- Fully atomic
- Reboot-free
- Using `pacman` as the underlying software perform the upgrade.

## Fully atomic

This might be obvious. But I'll define it here nonetheless. "Fully atomic" in
this context means that if an upgrade gets aborted for whatever reason the
result would be as if the upgrade never took place. This means that the system
will either be upgraded or not upgraded without any inconsistencies.

## Reboot-free

Other systems that uses OSTree for atomic upgrades require the system to reboot
for the changes take effect. This is good when you want to have an immutable
system. However, the point of this project is not to make an immutable system,
but just to make uprades to a system atomic.

It might be that OSTree just isn't designed to be able to do that in an
efficient way. If that is the case then I'll just have to find another way to
do this.

## Using pacman

This might very well change in the future, but the scope of this PoC is just to
figure out what needs to be done in order for this kind of system to work
satisfactory both regarding safety and user-friendliness. Since `pacman` knows
everything there is to know about how to install arch packages this PoC will
take advantage of that as a wrapper ontop of `pacman`.

