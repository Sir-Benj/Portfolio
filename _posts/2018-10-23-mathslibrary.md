---
title: "Maths Library (ongoing)"
date: 2018-10-23
tags: [c++, development]
header:
    image: "images/cpplogo.png"
excerpt: "Maths Library, understanding games engines."
---

As part of my continued development in c++, and to help develop my maths skills, I'm creating a basic maths for games library. A lot of the base code for this is from "Foundations of Game Engine Development - Volume 1, Mathematics" by Eric Lengyel. It's a fantastic textbook (my own find, not university proscribed), and shows in fantastic detail what kind of maths is needed for 3D engine development.

For my own library I've split the mathematical functions into headers and source files that make sense based on what each section covers, for example; 3D vectors, 3x3 matrices etc. I've also added some functions that aren't covered, like 2D vectors and matrices and some 4D structures.

Below is a code example from the library.

```c++

#pragma once
#include "Matrix3x3.h"
#include "Vector3D.h"

namespace mffg
{

	Matrix3X3::Matrix3X3() = default;

	Matrix3X3::~Matrix3X3() {}

	Matrix3X3::Matrix3X3(float n00, float n01, float n02,
		float n10, float n11, float n12,
		float n20, float n21, float n22)
	{
		n[0][0] = n00; n[0][1] = n01; n[0][2] = n02;
		n[1][0] = n10; n[1][1] = n11; n[1][2] = n12;
		n[2][0] = n20; n[2][1] = n21; n[2][2] = n22;
	}


	Matrix3X3::Matrix3X3(const Vector3D & a, const Vector3D & b, const Vector3D & c)
	{
		n[0][0] = a.x; n[0][1] = a.y; n[0][2] = a.z;
		n[1][0] = b.x; n[1][1] = b.y; n[1][2] = b.z;
		n[2][0] = c.x; n[2][1] = c.y; n[2][2] = c.z;
	}

	float& Matrix3X3::operator ()(int i, int j)
	{
		return (n[j][i]);
	}

	const float& Matrix3X3::operator ()(int i, int j) const
	{
		return (n[j][i]);
	}

	Vector3D& Matrix3X3::operator [](int j)
	{
		return (*reinterpret_cast<Vector3D*>(n[j]));
	}

	const Vector3D& Matrix3X3::operator [](int j) const
	{
		return (*reinterpret_cast<const Vector3D*>(n[j]));
	}

	Matrix3X3 operator *(const Matrix3X3& A, const Matrix3X3& B)
	{
		return (Matrix3X3(A(0, 0) * B(0, 0) + A(0, 1) * B(1, 0) + A(0, 2) * B(2, 0),
			A(0, 0) * B(0, 1) + A(0, 1) * B(1, 1) + A(0, 2) * B(2, 1),
			A(0, 0) * B(0, 2) + A(0, 1) * B(1, 2) + A(0, 2) * B(2, 2),
			A(1, 0) * B(0, 0) + A(1, 1) * B(1, 0) + A(1, 2) * B(2, 0),
			A(1, 0) * B(0, 1) + A(1, 1) * B(1, 1) + A(1, 2) * B(2, 1),
			A(1, 0) * B(0, 2) + A(1, 1) * B(1, 2) + A(1, 2) * B(2, 2),
			A(2, 0) * B(0, 0) + A(2, 1) * B(1, 0) + A(2, 2) * B(2, 0),
			A(2, 0) * B(0, 1) + A(2, 1) * B(1, 1) + A(2, 2) * B(2, 1),
			A(2, 0) * B(0, 2) + A(2, 1) * B(1, 2) + A(2, 2) * B(2, 2)));
	}

	float Determinant(const Matrix3X3& M)
	{
		return (M(0, 0) * (M(1, 1) * M(2, 2) - M(1, 2) * M(2, 1))
			  + M(0, 0) * (M(1, 1) * M(2, 2) - M(1, 2) * M(2, 1))
			  + M(0, 0) * (M(1, 1) * M(2, 2) - M(1, 2) * M(2, 1)));
	}
}

```

This code is part of the source file for the Vector 3D class and contains most of the functions I've learned about so far. Doing this has also taught me some more of the syntax for c++ and what you can do, for example; `inline` and `reinterpret_cast`.

I'll be continuing to build on this library throughout the year and update it regularly.