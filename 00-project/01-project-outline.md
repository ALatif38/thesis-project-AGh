---
name: Abdellatif Rabah Gherbi
neptun: AM0MKL
id: 2026-LG-01
github: https://github.com/ALatif38/thesis-project-AGh
supervisor: Gergely Laborci
---

# Multitrack Podcast Video Editor

## 1. Project Overview

Podcast production frequently involves multiple participants recorded using separate microphones and cameras. These recordings must be synchronised and edited to produce a coherent final video.

Manually managing multiple recordings can be time-consuming, particularly when editors need to switch between speakers, combine audio sources, and remove unwanted conversation segments.

The Multitrack Podcast Video Editor aims to simplify this workflow through a dedicated desktop application that organises recordings by participant and provides timeline-based editing tools.

The application will allow users to synchronise audio and video sources, select visible video tracks, mix audible audio tracks, remove unwanted sections, preview edits, and export the final composition locally.

## 2. Project Objectives

The primary objective is to develop a functional desktop application for managing and composing multitrack podcast recordings.

Specific objectives include:

- Provide user registration and authentication.
- Allow users to create, open, and manage editing projects.
- Import multiple audio and video recordings.
- Support video recordings containing usable audio.
- Assign source recordings to individual participants.
- Synchronise recordings using a common timeline zero point.
- Remove unwanted intervals from the conversation.
- Select which video track is visible at different timeline positions.
- Select one or more audible audio tracks.
- Mix audio tracks with adjustable gain.
- Apply default pan and zoom transformations to video tracks.
- Override video transformations at selected timeline points.
- Preview the edited composition.
- Export the final video locally.
- Provide a voice-only audio export option.
- Persist project metadata and editing decisions.
- Handle invalid media files and rendering failures.

## 3. Target Users

The intended users are:

- Podcast creators recording multiple participants.
- Content creators producing interview videos.
- Small podcast production teams.
- Students and independent creators working with separate audio and video sources.

The application is intended for users who need a focused podcast editing workflow rather than a complete professional video post-production suite.

## 4. Main User Workflow

A typical user will:

1. Register or log in to the application.
2. Create a new podcast editing project.
3. Import audio and video source files.
4. Assign recordings to their respective participants.
5. Define synchronisation offsets using a common zero point.
6. Review the recordings on a shared timeline.
7. Mark unwanted intervals for removal.
8. Select the visible video track for each relevant interval.
9. Select and mix audible audio tracks.
10. Adjust audio gain and video pan/zoom settings.
11. Preview the resulting composition.
12. Export the final video or voice-only audio.
13. Save and reopen the project to continue editing.

## 5. Project Scope

### Included Features

- User accounts and project management.
- Audio and video source management.
- Participant-based track organisation.
- Manual source synchronisation.
- Shared timeline editing.
- Removal of unwanted recording intervals.
- Audio and video track selection.
- Multiple audio-track mixing with gain adjustment.
- Default video pan/zoom transformations and timeline overrides.
- Local media preview and rendering.
- Video and voice-only export.
- Persistent project data.
- Input validation and error handling.

### Outside the Scope

The following features are not required for the initial implementation:

- General-purpose video post-production.
- Intro and outro creation.
- Advanced visual effects.
- Automatic subtitle generation.
- Automatic face tracking.
- Automatic audio synchronisation.
- Multiple simultaneous video layouts.

These may be considered as future extensions where appropriate.

## 6. Proposed Technical Direction

The application will use JavaScript or TypeScript and a desktop application framework such as Electron or Tauri.

The architecture will separate the user interface, project data management, timeline editing logic, and media-processing components.

The project will investigate browser-based media APIs and native media-processing tools to determine a suitable approach for preview and local rendering.

Project metadata, source-track information, synchronisation offsets, and editing decisions will be stored persistently.

The selected implementation technologies and supported media formats will be justified during the specification and technical design phases.

## 7. Measurable Success Criteria

The project will be considered successful when:

1. A user can create an account and manage multiple projects.
2. A project can contain at least two independently recorded media sources.
3. Sources can be assigned to participants and manually synchronised.
4. Unwanted timeline intervals can be excluded from the final output.
5. The user can select the visible video source at different timeline positions.
6. Multiple audio sources can be mixed with individually adjustable gain.
7. Video pan/zoom defaults and timeline overrides can be configured.
8. The application can preview a composition based on saved editing decisions.
9. The application can render a video file locally.
10. The application can export a voice-only version.
11. Saved projects can be reopened with their editing decisions preserved.
12. Unsupported media and rendering errors produce meaningful feedback.

## 8. Main Challenges and Risks

### Media Synchronisation

Separate recordings may have different starting points and durations.

The application must represent synchronisation offsets consistently so that preview and rendering use the same timing decisions.

### Media Processing Performance

High-resolution video and multiple audio sources can require significant processing resources.

The project will evaluate performance limitations and define practical constraints for supported input formats and export settings.

### Timeline Data Consistency

Cuts, source selections, audio gain, and video transformations must remain consistent when a project is saved and reopened.

A structured edit-decision model will be developed to support reproducible results.

### Rendering Reliability

Media files may be unsupported, corrupted, or unavailable.

The application will validate inputs, report failures clearly, and avoid treating incomplete exports as successful results.

## 9. Expected Outcome

The expected result is a working, version-controlled desktop application that supports the complete core workflow of multitrack podcast editing.

Users will be able to manage source recordings, synchronise them, define timeline-based editing decisions, preview the composition, and export the resulting video or voice-only audio locally.

The final project will include technical documentation, implementation decisions, testing results, and a reproducible development workflow.

## 10. Project Information

**Project Title:** Multitrack Podcast Video Editor

**Project ID:** 2026-LG-01

**Student:** Abdellatif Rabah Gherbi

**Supervisor:** Gergely Laborci

**Repository:** https://github.com/ALatif38/thesis-project-AGh

**Current Phase:** Project planning and requirements analysis.
