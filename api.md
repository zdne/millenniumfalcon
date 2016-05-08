# Millennium Falcon ([Spacecraft][])

## Properties
- `crew` (array[[Person][]])
- `passengers` (array[[Person][]])
- `escape_crafts` (array[[Escape Craft][]])
- `armament`
- `engine`
- `hyperdrive`
- `communication_systems`
- `hatches`
- `shields`
- `cargo`

## Affordances
- `takeOff`
	- Conditions
		- `crew` > 2

- `land`
- `enterHyperspace`
- `leaveHyperspace`
- `setControl`
	- Parameters
		- `pitch`
		- `roll`
		- `yaw`

- `setThrust`
	- Parameters
		- `thrust`

- `embark`
	- Parameters
		- `person` ([Person][])
		- `role` (enum)
			- `crew`
			- `passenger`

- `disembark`
	- Parameters
		- `person` ([Person][])

## States
- `landed` (entry)
	- `takeOff` -> `airborne`
	- `addCrewMember` -> `landed`
	- `removeCrewMember` -> `landed`

- `airborne`
	- `land` -> `landed`
	- `enterHyperspace` -> `hyperspaceborne`
	- `setControl` -> `airborne`
	- `setThrust` -> `airborne`

- `hyperspaceborne`
	- `leaveHyperspace` -> `airborne`

# Person
## Properties
- `name`

# Universe
Everything in the Star Wars universe.

## Properties
- `people` (array[[Person][]])
- `space_crafts` (array)

## Affordances
- `createPerson`
	- Parameters
		- `person` ([Person][])

- `removePerson`
	- Parameters
		- `person` ([Person][])

# Escape Craft ([Spacecraft][])
Model CEC Class-1 escape craft.

## Properties
- `crew` (array[[Person][]])
- `passengers` (array[[Person][]])
- `host`

## Affordances
- `launch`
- `land`

## States
- `docked` (entry)
	- `launch` -> `airborne`

- `airborne`
	- `land` -> (end)

# Spacecraft
The abstract base class for any spacecraft.

---

[Person]: #person
[Escape Craft]: #escape-craft
[Spacecraft]: #spacecraft
