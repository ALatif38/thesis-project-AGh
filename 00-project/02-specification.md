---
project_outline: "[[00-project/01-project-outline]]"
project_id: 2026-LG-01
student: Abdellatif Rabah Gherbi
supervisor: Gergely Laborci
status: Draft for supervisor review
---

# Multitrack Podcast Video Editor

## Project Specification

**Project ID:** 2026-LG-01  
**Student:** Abdellatif Rabah Gherbi  
**Supervisor:** Gergely Laborci

This document defines the proposed functional behaviour, data requirements, user interactions, and technical constraints of the Multitrack Podcast Video Editor.

The specification describes the intended application and is subject to supervisor feedback. Implementation technologies and performance limits will be refined during development.

---

## 1. System Overview

The Multitrack Podcast Video Editor is a desktop application for preparing podcast recordings captured using separate audio and video sources.

The application allows users to organise recordings by participant, synchronise them on a shared timeline, remove unwanted conversation intervals, select audible audio tracks and visible video tracks, preview editing decisions, and export the resulting composition.

Media processing and rendering will take place locally on the user's device.

The application focuses on podcast content preparation rather than general-purpose video post-production.

## 2. Actors and Permissions

| Actor | Description | Permissions |
|---|---|---|
| Visitor | User without an account | Register and log in |
| Registered User | Authenticated application user | Create, edit, save, and export personal projects |
| Project Owner | Registered user who owns a project | Manage project sources, participants, and editing decisions |

Each user must only be able to access projects they are authorised to manage.

## 3. Functional Requirements

### FR-01 — User Registration and Authentication

The system shall allow users to:

- Register an account.
- Log in using valid credentials.
- Log out securely.
- Access their own projects after authentication.

Invalid credentials must produce an appropriate error message.

### FR-02 — Project Management

The system shall allow authenticated users to:

- Create a new editing project.
- Assign a project name.
- View existing projects.
- Open and modify saved projects.
- Rename projects.
- Delete projects after confirmation.

Project metadata must be stored persistently.

### FR-03 — Media Import

The system shall allow users to:

- Import audio recordings.
- Import video recordings.
- Import video recordings containing usable audio.
- Add multiple recordings to one project.
- View imported source metadata.
- Remove a source from the project.

The system must validate imported files and report unsupported or invalid media.

### FR-04 — Participant Management

The system shall allow users to:

- Create participant entries.
- Assign source recordings to participants.
- Change source assignments.
- View recordings grouped by participant.

A participant may have multiple associated sources.

### FR-05 — Media Synchronisation

The system shall provide a shared timeline for all imported recordings.

Users shall be able to:

- Define a common timeline zero point.
- Set a synchronisation offset for each source.
- Adjust offsets manually.
- Preview synchronised recordings.
- Save synchronisation settings.

All editing decisions must use a consistent timeline reference.

### FR-06 — Timeline Editing

The system shall provide a timeline-based editing interface.

Users shall be able to:

- Navigate through the recording timeline.
- Define intervals that should be removed.
- Modify or delete previously defined cuts.
- Select which video source is visible during an interval.
- Select which audio sources are audible during an interval.

Editing decisions must remain consistent when the project is reopened.

### FR-07 — Audio Selection and Mixing

The system shall support:

- Selection of one or more audible audio tracks.
- Simultaneous mixing of selected audio sources.
- Adjustable gain for individual audio tracks.
- Audio extracted from video sources when usable.
- Preservation of audio settings in the project data.

The preview and final export must follow the same audio-selection decisions.

### FR-08 — Video Selection and Transformations

The system shall allow users to:

- Select one visible video track at a time.
- Configure a default pan and zoom transformation for each video source.
- Override transformations at defined timeline points.
- Preview the selected framing.

Multiple simultaneous video layouts are considered an optional extension.

### FR-09 — Preview

The system shall provide a preview of the edited composition.

The preview must reflect:

- Synchronisation offsets.
- Removed intervals.
- Visible video selection.
- Audible audio selection.
- Audio gain.
- Video pan and zoom transformations.

The preview should allow users to inspect their editing decisions before export.

### FR-10 — Local Rendering and Export

The system shall allow users to:

- Render the edited composition as a video file.
- Export a voice-only audio version.
- Choose an output destination.
- View rendering progress or status.
- Receive confirmation when rendering succeeds.
- Receive an error message when rendering fails.

Media rendering must take place on the client device.

### FR-11 — Data Persistence

The application shall persist:

- User account information.
- Project metadata.
- Participant information.
- Source-track metadata.
- Synchronisation offsets.
- Timeline cuts.
- Audio and video selections.
- Audio gain values.
- Video transformation defaults and overrides.

Reopening a project must restore its editing decisions.

### FR-12 — Validation and Error Handling

The application shall detect and report:

- Unsupported media formats.
- Corrupted or unreadable media.
- Missing source files.
- Invalid timeline intervals.
- Invalid synchronisation settings.
- Failed project loading or saving.
- Failed media rendering.

Error messages should explain the problem and, where possible, suggest a corrective action.

---

## 4. Use Cases

### UC-01 — Create a Project

**Actor:** Registered User

**Precondition:** The user is authenticated.

**Main Flow:**

1. The user selects "Create Project".
2. The application requests a project name.
3. The user enters a valid name.
4. The application creates the project.
5. The project appears in the user's project list.

**Expected Result:** A new project is created and stored successfully.

### UC-02 — Import and Assign Recordings

**Actor:** Project Owner

**Main Flow:**

1. The user opens an existing project.
2. The user selects "Import Media".
3. The user chooses audio or video files.
4. The application validates the files.
5. The application displays the imported sources.
6. The user assigns each source to a participant.

**Expected Result:** Imported recordings are available for timeline editing.

### UC-03 — Synchronise Sources

**Actor:** Project Owner

**Main Flow:**

1. The user opens the timeline.
2. The user identifies a common reference point.
3. The user adjusts source synchronisation offsets.
4. The application updates source positions.
5. The user previews the synchronised recordings.
6. The user saves the project.

**Expected Result:** Recordings are aligned according to the saved offsets.

### UC-04 — Edit Podcast Content

**Actor:** Project Owner

**Main Flow:**

1. The user navigates through the timeline.
2. The user marks an unwanted interval.
3. The application excludes the interval from the composition.
4. The user selects the visible video track.
5. The user selects audible audio tracks.
6. The user adjusts gain and video framing.
7. The user previews the result.

**Expected Result:** The composition reflects the user's editing decisions.

### UC-05 — Export the Composition

**Actor:** Project Owner

**Main Flow:**

1. The user opens the export interface.
2. The user selects video or voice-only output.
3. The user chooses an output destination.
4. The application validates the project.
5. The application renders the composition locally.
6. The application reports the export result.

**Expected Result:** A playable output file is generated when rendering succeeds.

---

## 5. Timeline and Data Model

The application will use a structured representation of source recordings and editing decisions.

### 5.1 User

A user record contains:

- Unique user identifier.
- Authentication information.
- Account creation information.

Passwords must not be stored in plaintext.

### 5.2 Project

A project contains:

- Unique project identifier.
- Project owner.
- Project name.
- Creation and modification timestamps.
- Participant records.
- Source-track references.
- Timeline editing decisions.
- Export settings.

### 5.3 Participant

A participant contains:

- Unique participant identifier.
- Display name.
- Associated source tracks.

### 5.4 Source Track

A source track contains:

- Unique source identifier.
- Associated participant.
- Source file reference.
- Media type.
- Duration.
- Relevant audio/video metadata.
- Synchronisation offset.
- Default video transformation.

Source files will be referenced rather than embedded directly into the project metadata.

### 5.5 Timeline Edit Decision

An editing decision contains:

- Timeline start and end positions.
- Whether the interval is retained or removed.
- Selected visible video source.
- Selected audible audio sources.
- Audio gain settings.
- Applicable video transformation overrides.

### 5.6 Time Representation

Timeline positions and synchronisation offsets will use a consistent time representation.

The selected precision and rounding strategy will be documented to minimise differences between preview and rendering.

### 5.7 Reproducibility

Editing decisions will be stored independently of the preview interface.

When a project is reopened, the application will reconstruct the timeline using the saved source references, synchronisation offsets, cuts, track selections, and transformation settings.

If a source file is missing, the application will report the problem rather than silently replacing the source.

---

## 6. Non-Functional Requirements

### NFR-01 — Usability

The interface should provide an understandable workflow for importing, synchronising, editing, previewing, and exporting podcast recordings.

### NFR-02 — Performance

The application should remain responsive during normal editing operations.

Practical media-resolution, track-count, and rendering-performance limits will be determined through testing.

### NFR-03 — Reliability

The application must preserve saved editing decisions and report unsuccessful operations.

### NFR-04 — Security

User authentication data must be handled securely.

Secrets and access tokens must not be committed to the public repository.

### NFR-05 — Maintainability

The source code should separate interface logic, project management, timeline processing, and media rendering.

### NFR-06 — Local Processing

Media preview and rendering must execute on the client device.

### NFR-07 — Portability

The application will use a JavaScript or TypeScript desktop framework.

Supported operating systems will be defined according to the selected framework and available testing environment.

---

## 7. Proposed Architecture

The application is expected to contain the following components:

1. **Desktop User Interface**
   - Project management.
   - Media import.
   - Participant management.
   - Timeline editing.
   - Preview and export controls.

2. **Project Data Layer**
   - Persistent project metadata.
   - Source-track information.
   - Editing decisions.
   - User account information.

3. **Timeline Processing Layer**
   - Synchronisation offsets.
   - Cut handling.
   - Audio and video selection.
   - Gain and transformation settings.

4. **Media Processing Layer**
   - Source decoding.
   - Audio mixing.
   - Video composition.
   - Preview generation.
   - Local rendering and export.

The final component boundaries and technologies will be refined during technical design.

---

## 8. Media Processing Research

The project will compare suitable client-side media-processing approaches.

### Browser-Based APIs

Potential technologies include:

- HTMLMediaElement.
- Web Audio API.
- Canvas.
- WebCodecs, where supported.

These technologies may provide interactive preview capabilities but have limitations related to format support, performance, and export workflows.

### Native Media Processing

A native media-processing solution such as FFmpeg may provide broader decoding, filtering, mixing, and encoding capabilities.

However, native tooling introduces additional packaging, integration, and platform considerations.

### Selection Criteria

The final approach will be evaluated according to:

- Supported input formats.
- Audio mixing capabilities.
- Video transformations.
- Preview responsiveness.
- Rendering reliability.
- Desktop integration.
- Performance.
- Maintainability.

The preview and export pipelines must interpret the same saved editing decisions.

---

## 9. Export Assumptions

The initial implementation will prioritise a limited, documented set of supported source and output formats.

The final export specification will define:

- Supported input containers and codecs.
- Video output container and codec.
- Audio output format.
- Resolution assumptions.
- Frame-rate handling.
- Audio sample-rate handling.
- Rendering limitations.

The application must validate media compatibility before attempting an export.

---

## 10. Acceptance Criteria

The core implementation will be accepted when the following can be demonstrated:

| ID | Acceptance Criterion |
|---|---|
| AC-01 | A user can register and authenticate. |
| AC-02 | A user can create and reopen a project. |
| AC-03 | Multiple media sources can be imported. |
| AC-04 | Sources can be assigned to participants. |
| AC-05 | Synchronisation offsets can be configured and saved. |
| AC-06 | Unwanted timeline intervals can be removed. |
| AC-07 | Visible video selection can change across the timeline. |
| AC-08 | Multiple audio sources can be mixed with adjustable gain. |
| AC-09 | Video pan/zoom defaults and overrides are supported. |
| AC-10 | A preview reflects saved editing decisions. |
| AC-11 | A video composition can be rendered locally. |
| AC-12 | A voice-only output can be exported. |
| AC-13 | Projects reopen with editing decisions preserved. |
| AC-14 | Invalid media and rendering failures produce meaningful errors. |

---

## 11. Possible Extensions

The following features may be considered after the required functionality is complete:

- Automatic signal-based synchronisation.
- Multiple simultaneous video layouts.
- Audio fades and advanced audio processing.
- Non-identifying face tracking for automatic framing.
- Subtitle generation.
- Social-media export presets.

These features are not required for the initial implementation.

---

## 12. Development and Validation Strategy

Development will proceed incrementally.

The proposed stages are:

1. Requirements analysis and technical research.
2. Architecture and timeline data-model design.
3. Desktop application setup.
4. User and project management.
5. Media import and participant management.
6. Manual synchronisation and timeline editing.
7. Audio mixing and video selection.
8. Preview implementation.
9. Local rendering and export.
10. Testing, documentation, and refinement.

Testing will include representative audio/video sources, multiple participants, timeline cuts, project reopening, and invalid input scenarios.

---

## 13. Current Status

**Project Phase:** Requirements analysis and specification.

This document describes the proposed behaviour of the application.

Implementation decisions, supported formats, and performance limits remain subject to technical evaluation and supervisor feedback.
